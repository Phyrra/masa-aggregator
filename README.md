Installation
============

The module is registered on npm, to install run
```
yarn add sama-aggregator
```

Since the library is written in Typescript, it comes with its own types.

Usage
=====

For full documentation, please refer to https://aggregator.000webhostapp.com/

Examples
========

### Fitering Data

#### A flat list
```
new Aggregator([1, 2, 3, 4, 5])
	.where(function(item) {
		return item % 2 === 0;
	})
	.toArray();
```

#### A list of objects
```
new Aggregator([
	{
		name: 'Adam',
		location: {
			city: 'Zurich',
			country: 'Switzerland'
		}
	}, {
		name: 'Beat',
		location: {
			city: 'Basel',
			country: 'Switzerland'
		}
	}, {
		name: 'Clair',
		location: {
			city: 'Bishkek',
			country: 'Kyrgyztan'
		}
	}
])
	.where('location.country', eq('Switzerland'))
	.toArray();
```

### Grouping

```
new Aggregator([
	{ gender: 'M', name: 'Adam' },
	{ gender: 'M', name: 'Beat' },
	{ gender: 'F', name: 'Clair' },
	{ gender: 'F', name: 'Delilah' }
])
	.group('gender')
	.toMap();
```
