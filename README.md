# The Magical CSV Merge Machine

## What does it do ?

A python3 library to link a dirty CSV file with a clean reference table. It is meant to as generic as possible and includes a labeller to learn optimal parameters for each matching scenario.

![Alt Text](documentation/labeller_peek.gif)

## How to install ?

### Manual install

#### Non-Python Requirements

This library relies on Elasticsearch. We used version 5.6.7 for developpment.. We recommend Elasticsearch 5.X. Instructions [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/_installation.html).

#### PIP3 install

```
pip3 install merge-machine
```

From source (recommended, for the meantime...):
```
git clone https://github.com/entrepreneur-interet-general/Merge-Machine.git
cd Merge-Machine
pip3 install -e .
```

## How to use ?

### General use example (install the package first...)
See [examples/example.py](https://github.com/eig-2017/Merge-Machine/blob/master/examples/example.py).

### Resource creation example (to use advanced analyzers)
See [examples/gen\_resource\_example.py](https://github.com/eig-2017/Merge-Machine/blob/master/examples/gen_resource_example.py).

### Guidelines
See [HOW\_TO.md](https://github.com/eig-2017/Merge-Machine/blob/master/HOW_TO.md).

## How it works ?

The reference is indexed in Elasticsearch with multiple analyzers (languages specific, integers, n\_grams...). The labeller then proposes training samples from the source which it tries to match to rows of the reference file. Upon user confirmation (match / not match) it updates its belief on which Elasticsearch queries are most performant to use for matching. When labelling is over, the "best query" (a weighted combination of multiple ES queries with different analyzers on different fields) is used for each row of the source to try to find a match in the ES-indexed referential.

## How to contribute ?

Feel free to report bugs via issues and make pull requests...

## Credits

This library was developped by Léo Bouloc during 10 months in 2017 at the French [Ministry of Research and Higher Education](http://www.enseignementsup-recherche.gouv.fr/) in the context of the ["Entrepreneur d'Intérêt Général" program](https://www.etalab.gouv.fr/decouvrez-la-1e-promotion-des-entrepreneurs-dinteret-general) funded by the French Government.

## See also

This library was developped as a component of larger matching service:
* ONLINE SERVICE COMING SOON !!!
* [code](https://github.com/eig-2017/the-magical-csv-merge-machine)

Check out:
* [The Merge Machine](https://themergemachine.com), A simple web interface to link your data

Other similar libraries include:
* [match_id](https://github.com/matchID-project) (Identity record linking)
* [dedupe](https://github.com/dedupeio/dedupe) (Record linking and deduping)
