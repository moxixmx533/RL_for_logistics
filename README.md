# gym-warehouse
A gym environment representing a chaotic warehouse.

Details about this implementation:

State:

-Agent Position    
-Agent Status    
-StagingIn    
-StagingOut    
-BinStatus    
-Timestep     


This implementation uses a Box Space (Continuous Space) instead of a Multidiscrete space, but applies a one-hot encoding to all the
variables except the Timestep.

Actions:
LEFT,RIGHT,UP,DOWN + Agent_slots x bin_slots 

Particularities    
-No Stay Command    
-Sparse Rewards with only 'completion of an OUTBOUND transaction'    
-Random Transactions (either outbound or inbound sensible transactions are generated when a transaction is completed)    
-Timestep as part of the state    
-The staging-out-area.status details what items are MISSING to complete the transaction    




## Setup
Make sure you have Python 3.6 or later installed.

1. Clone the repo
```
git clone git@gitlab.lrz.de:dilab-20-multi-agent-rl/gym-warehouse.git
cd gym-warehouse
```
2. Create a new virtual environment
```
python3 -m venv .venv
source .venv/bin/activate
```
3. Install the dependencies
```
pip install --upgrade pip wheel
pip install -r requirements.txt
```
4. Install the environment in development mode
```
pip install -e .
```

## Running
You can use the `main.py` script to train a DQN on a warehouse.
For example, you can train a DQN on the `two-slots.json` environment for
`200000` steps and with an exploration fraction of `0.3` and save the model
into a file called `my-model.zip` by running
```
python main.py --train --steps 200000 --explore 0.2 two-slots my-model
```
Or, using the short versions,
```
python main.py -t -s 200000 -e 0.2 two-slots my-model
```
Your model will be saved to the `models` directory.
To watch its performance, you can run
```
python main.py two-slots my-model
```
To see a list of all options, run
```
python main.py -h
```

## Documentation
You can generate documentation for the entire project by running `make html`
in the `docs` directory. You should now be able to find a file called
`index.html` in `docs/build/html`. Open it with your favorite browser to browse
the documentation.

Note: you need to have `make` installed for this.
