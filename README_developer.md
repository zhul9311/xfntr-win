# Development log
## 1. Add command script: xfntr
Use "entry_points" keyword in setup() to add command "xfntr" in ocmmand line. There might be path problems.

```
entry_points = { # create scripts and add to sys.PATH
        'console_scripts':[
            'xfntr1 = xfntr.main:main'
        ],
        'gui_scripts': [
            'xfntr = xfntr.main:main'
        ]
    }
```

## 2. Solve path issue

Command line might not be albe to find the right path where the module is. In main.py, added the following so it can find module mainwindow.py

```
import os
# Use absolute path instead of relative path ('./') to avoid trouble when installed by pip
dir_path = os.path.dirname(os.path.realpath(__file__))
sys.path.append(dir_path)
```

In mainwindow.py, added the following

```
import os
# Use absolute path instead of relative path ('./') to avoid trouble when installed by pip
dir_path = os.path.dirname(os.path.realpath(__file__))
```
and used the absolute file path for GUI files: 

```
UI_path = dir_path + '/GUI/'
```

## 3. Compatability with Windows OS. (Version: 0.2.6)
Rewrote "parratt function" in python and removed all fortran code dependencies. Used `Numba` package to speed up the python function.

## 4. Modify the model to account for the penetration through the glass wall. 

<img src="/Users/zhuzi/Documents/work/XFNTR%20project/md_files/20200308.png" alt="Kitten"
	title="A cute kitten" width="150" height="100" />

---

## Future Ideas
1. Rewrite the core function in c and call it from python. 
    1. Learn array in C.
    1. Write test code.
1. Think of implementing 2D fitting in (qz,sh) space.
    1. \[x] Core function is ready for 2D calculation.
    1. Implement 3D plot to plot surface in (qz,sh) space.
    1. Identify which part of data is sensitive to a particular parameter.
    1. Propose a measurement procedure.
1. Implement parallel computing.
1. Add function for simple calculations. For example:
    1. Electron density calculation
    
