# Welcome to the contributing guidelines !
Want to contribute to XGen library ? That is cool! Thank you! :smile:

## Contributing guidelines

If you want to contribute to this repo, please consider following this checklist

1) Fork this repo
2) Clone it on your local drive and install the library in editable mode
```bash
$ git clone git@github.com:XgenTimeSeries/xgen-timeseries.git
$ cd xgen-timeseries
$ pip install -e .
```
3) Create a branch with an explicit name of your contribution
```bash
$ git checkout -b my_branch_with_contribution
```
4) Make sure you add the appropriate tests to test your feature. If the library test coverage reduces
significantly, the contribution will raise some red flags.

5) Ensure that your contribution passes the existing test suite by running
```bash
pytest tests/
``` 
- Polish your contribution using black and isort


## Any doubts ?
In any case if you have any question, do not hesitate to reach out to me directly, I will be happy to help! :smile:
