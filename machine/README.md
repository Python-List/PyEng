File: calc_correlation.py

Error: print
Cause: Usage of print Python 2 style
Solution: correct to use the Python 3 style

File: ml_main.py

Error: print
Cause: Usage of print Python 2 style
Solution: correct to use the Python 3 style

Warning: use of corr_dict.py, if it has not been generated through calc_correlation.py, invalid results would occur
Solution: import calc_correlation.py into ml_main.py, and call the find_correlations, possibly with an argument at false by default
to say wether we need to compute the said correlations or not.

Note: Using the syntax if __name__ = "__main__" would improve the readability and flexibility of the code