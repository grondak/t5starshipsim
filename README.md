# t5starshipsim
A discrete-event simulator for starship travel

The Traveller game in all forms is owned by Mongoose Publishing. Copyright 1977 – 2024 Mongoose Publishing. [Fair Use Policy](https://cdn.shopify.com/s/files/1/0609/6139/0839/files/Traveller_Fair_Use_Policy_2024.pdf?v=1725357857)

There is a requirements.txt. I got it like this:
```bash
pip install pipreqs
pipreqs . --force
```

to use it:
```bash
python -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
```

then 

```bash
pip install -r requirements.txt
```

The python package's code is in `T5Code` and the tests are in the `tests` directory.

I use black to fix my quotes:
```bash
pip install black
black .
```

To test this code, you can do 
```bash
pip install pytest pytest-cov
pytest --cov=src/T5Code tests/
pytest --cov=src/T5Code --cov-report=html
```
then open `file:///htmlcov/index.html` in a browser

Looking for TDD'd code, look no further.
```
======================================================================================= tests coverage =======================================================================================
______________________________________________________________________ coverage: platform darwin, python 3.12.3-final-0 ______________________________________________________________________

Name                               Stmts   Miss  Cover
------------------------------------------------------
src/T5Code/GameState.py               23      2    91%
src/T5Code/T5Basics.py                22      0   100%
src/T5Code/T5Lot.py                   63      0   100%
src/T5Code/T5Mail.py                  18      0   100%
src/T5Code/T5NPC.py                   25      0   100%
src/T5Code/T5RandomTradeGoods.py     158      0   100%
src/T5Code/T5ShipClass.py             11      0   100%
src/T5Code/T5Starship.py             129      0   100%
src/T5Code/T5Tables.py                 6      0   100%
src/T5Code/T5World.py                 40      0   100%
------------------------------------------------------
TOTAL                                495      2    99%
===================================================================================== 97 passed in 0.18s =====================================================================================
```
There is a test simulator/Game called GameDriver.py.
Run it like this:
```bash
python examples/GameDriver.py
```
It outputs a journal of activities taken by one starship.

This code will eventually be used by a simpy discrete-event simulation of thousands of starships in an Imperium.