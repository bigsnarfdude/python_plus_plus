python_plus_plus
==============

C++ Apache Log Parser built with [pybind11](https://github.com/pybind/pybind11).

Installation
------------

**On Unix (Linux, OS X)**

 - `pip install pybind11`
 - clone this repository
 - `pip install ./python_plus_plus`

**On Windows (Requires Visual Studio 2015)**

 - For Python 3.5:
     - clone this repository
     - `pip install ./python_plus_plus`
 - For earlier versions of Python, including Python 2.7:

   Pybind11 requires a C++11 compliant compiler (i.e. Visual Studio 2015 on
   Windows). Running a regular `pip install` command will detect the version
   of the compiler used to build Python and attempt to build the extension
   with it. We must force the use of Visual Studio 2015.

     - clone this repository
     - `"%VS140COMNTOOLS%\..\..\VC\vcvarsall.bat" x64`
     - `set DISTUTILS_USE_SDK=1`
     - `set MSSdk=1`
     - `pip install ./python_example`

   Note that this requires the user building `python_plus_plus` to have registry edition
   rights on the machine, to be able to run the `vcvarsall.bat` script.


Windows runtime requirements
----------------------------

On Windows, the Visual C++ 2015 redistributable packages are a runtime
requirement for this project. It can be found [here](https://www.microsoft.com/en-us/download/details.aspx?id=48145).

If you use the Anaconda python distribution, you may require the Visual Studio
runtime as a platform-dependent runtime requirement for you package:

```yaml
requirements:
  build:
    - python
    - setuptools
    - pybind11

  run:
   - python
   - vs2015_runtime  # [win]
```


Building the documentation
--------------------------

Documentation for the example project is generated using Sphinx. Sphinx has the
ability to automatically inspect the signatures and documentation strings in
the extension module to generate beautiful documentation in a variety formats.
The following command generates HTML-based reference documentation; for other
formats please refer to the Sphinx manual:

 - `cd python_example/docs`
 - `make html`

Usage
---------

```python
import python_plus_plus as m

target_file = 'path/to/file'
m.add_target_file(target_file)
m.parse_file()
m.stats()
```
