Error: cannot import cv2
Cause: OpenCV library is not present
Solution: Build it (see second task!)
Or since menpo provides opencv3 for python 3.5 (could not find any support for Python 3.6 with Anaconda), create
a virtualenv (conda create -n python35 python=3.5.2), switch to it and install opencv (conda install -c menpo opencv3)

blur.py
Error: Python2 print style
Solution: Switch to Python3 style (print())

color_train.py, color_test.py
Error: Cannot import SimpleCV
Cause: SimpleCV not present
Solution: Switch to Python2, since Python3 is not supported yet. (another possibility would be to help make the portage)

Error: Unresolved reference raw_input
Cause: raw_input was changed to input in Python3
Solution: modify raw_input to input