# Inx-to-build-QuSpin-on-Windows
My dev environment does not use Anaconda or minianaconda.

This dev env used:
QuSpin-dev_0.3.7
VS2022 for C++ 64bit Version 17.2.5
boost_1_76_0  --- have not yet upgraded to 1 79 0
Python 3.10.5

Issue: Cmd window and powershell started from VS2022 did not work for an initial attempt at a build... ??????
I did not revisit this issue latter.

1.	Start a cmd window as admin
2.	Switch it to powershell >powershell
3.	Run C:"\Program Files\Microsoft Visual Studio\2022\Community\VC\Auxiliary\Build\vcvarsamd64_x86.bat"
4.  Edit various setup.py  ( this is a dirty way.. to adds a hard coded path to BOOST)
    if sys.platform == "win32":
        extra_compile_args=["-IC:\\temp\ThirdParties\Boost\\boost_1_76_0"]
    else:
        extra_compile_args=["-fno-strict-aliasing","-Wno-unused-variable","-Wno-unknown-pragmas","-std=c++11"]
        
    This is to change these files from this:
     if sys.platform == "win32":
        extra_compile_args=[]
     else:
        extra_compile_args=["-fno-strict-aliasing","-Wno-unused-variable","-Wno-unknown-pragmas","-std=c++11"]  
		
5.  run:
    python setup.py install --default-compiler-flags --record install_file.txt

6.  To run QuSpin-dev_0.3.7's example0.py	
	   pip install gmpy2
	
	   output from example0.py	:
	   Hermiticity check passed!
	   Symmetry checks passed!
	   Particle conservation check passed!
	   
