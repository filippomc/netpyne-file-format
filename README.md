# netpyne-file-format
Proposals for netpyne exchange format

## Load from Python

The loader function will be part of netpyne:

from netpyne import specs

### Scenario A
```python
netParams, simConfig = specs.load(index='index.npjson', method='python')    # optional argument: save_to_json=True
```

### Scenario B
```python
netParams, simConfig = specs.load(index='index.npjson', method='json')
```

## Generate an index from an existing NetPyNE model

A new utility allows the user to create the index file from command line

Interactive mode:
```
$ netpyne export . --interactive
> Interactive procedure to define export your NetPyNE model to the interchange format. Type ENTER on any question if not relevant or leaving the default value.

> Specify the network parameters file [src/netParams.py]: netParams.py
> Specify the network parameters variable [netParams]: netParams
> Specify the simulation configuration file [src/cfg.py]: cfg.py
> Specify the simulation configuration variable [netParams]: cfg
> Specify the mod files folder [mod]:
> Specify the cells files folder [cells]:
> Specify the simulation init (run) file [src/init.py]: 


> The index file index.npjson has been created
> The json specification file params/spec.json has been created
```

Argument-based mode:
```
$ netpyne export . --netParams-file=netParams.py --netParams-var=netParams --simConfig-file=cfg.py
> Exporting your NetPyNE model to the interchange format
> Network parameters (netParams.py:netParams) found. OK.
> Simulation configuration (cfg.py:cfg) found. OK.
> Initialization file (src/init.py) not found.
> mod folder (mod) found
> cells folder (cells) not found

> The index file index.npjson has been created
> The json specification file params/netParams.json has been created
> The json specification file params/cfg.json has been created
```

The script errors in the case that a necessary file is not found.