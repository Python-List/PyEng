File: obesity.py

Error: print
Cause: Usage of print Python 2 style
Solution: correct to use the Python 3 style

File: pandas_movie.py

Error: print
Cause: Usage of print Python 2 style
Solution: correct to use the Python 3 style

Error: UnicodeDecodeError: 'utf-8' codec can't decode byte 0xe9 in position 3: invalid continuation byte
Cause: The encoding of the file movie_lens/u.item is in "ISO-8859-1", however pandas by default uses "UTF-8", which results in
the decoding of the file failing.
Solution: add to the call read_csv(..., encoding = "ISO-8859-1")

Warnings: Calls to "order" and "sort" are deprecated
Solution: Follow the recommendation in the warning comment
