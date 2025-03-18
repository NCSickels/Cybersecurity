# Python TL;DR Guide

## Return Type Annotations

***Forward references*** in Python refer to type annotations for classes or types that have not yet been fully defined when the annotation is used. To indicate a forward reference, you should enclose the type name in quotes. This approach is beneficial when the class definition is incomplete or when there are circular dependencies between classes. Python will raise a `NameError` if the type name is not quoted because it attempts to resolve the type name immediately. 

For example: 

```python
class Hcurve:
	...
	@classmethod
	def fromSize(self, dimension, size) -> "Hcurve":
		...
```

## Init Python File

- The purpose of an `__init__.py` file in a Python package is to initialize the package and define what is accessible when the package is imported. Normally, this file is separately defined in a file within the directory of the program.   

```python title:"Example __init__.py File"
import asyncio 
from .settings import Settings
from .config import Config
```

- Additionally, you can use the list `__all__` inside of the `__init__.py` file to define the public interface of the package. This method specifies which names should be imported when a user imports the package using the `from package import *` syntax. By including these names, you are explicitly stating that these are the intended public components of the package.

```python title:"Example __init__.py with __all__"
import asyncio 
from .settings import Settings
from .config import Config
from .modules import Module

__all__ = ["Settings", "Config", "Module"]
```

## Docstrings
---
### One-Line Docstrings

One-line docstrings are short descriptions that fit on a single line. They are enclosed in triple quotes (`'''` or `"""`), and the *closing quotes must be on the same line*.

Although both triple-single and triple-double quotes work, the standard convention in Python is to use triple-double quotes (`"""`).

```python
def square(a):
    """Returns the square of the given number."""
    return a ** 2  # Corrected exponentiation

# Accessing the docstring
print(square.__doc__)
```

```text title:Output
Returns the square of the given number.
```

You can also retrieve the documentation using Python's `help()` function:
```python
help(square)
```

```text title:Output
Help on function square in module __main__:

square(a)
    Returns the square of the given number.
```

### Multi-Line Docstrings

Multi-line Docstrings also contain the same string literals line as in One-line Docstrings, but it is followed by a single blank along with the descriptive text.

The general format for writing a Multi-line Docstring is as follows:

```python
def some_function(argument1):
    """Summary or Description of the Function
    Parameters:
    argument1 (int): Description of arg1
    
    Returns:
    int:Returning value
   """
    return argument1

print(some_function.__doc__)
```

```python title:"Summary or Description of the Function"
    Parameters:
    argument1 (int): Description of arg1

    Returns:
    int:Returning value
```

```python
help(some_function)
```

```text title:Output
Help on function some_function in module __main__:

some_function(argument1)
    Summary or Description of the Function

    Parameters:
    argument1 (int): Description of arg1

    Returns:
    int:Returning value
```

### Docstrings in Classes
In a class definition, a docstring can be used to provide documentation for the class as a whole. You typically place it immediately after the class definition, and it is enclosed in triple quotes (`"""`). For example:

```python 

class MyClass:
    """This is the documentation for MyClass."""

    def __init__(self):
        """This is the documentation for the __init__ method."""
        pass
```

Docstrings can be accessed using the `__doc__` attribute of the class or method. For example, you could access the docstring for `MyClass` using `MyClass.__doc__`

### Docstring Formats

| **Formatting Type**      | **Description**                                                                                                                     |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| *NumPy/SciPy docstrings* | Combination of reStructured and GoogleDocstrings and supported by Sphinx                                                            |
| *PyDoc*                  | Standard documentation module for Python and supported by Sphinx                                                                    |
| *EpyDoc*                 | Render Epytext as series of HTML documents and a tool for generating API documentation for Python modules based on their Docstrings |
| *Google Docstrings*      | More intuitive and easier to use short form of docstring.                                                                           |

#### Sphinx Style

Sphinx is the easy and traditional style, verbose, and was initially created specifically for Python Documentation. Sphinx uses a reStructured Text, which is similar in usage to Markdown.

```python
class Vehicle(object):
    '''
    The Vehicle object contains lots of vehicles
    :param arg: The arg is used for ...
    :type arg: str
    :param `*args`: The variable arguments are used for ...
    :param `**kwargs`: The keyword arguments are used for ...
    :ivar arg: This is where we store arg
    :vartype arg: str
    '''
    def __init__(self, arg, *args, **kwargs):
        self.arg = arg
        
    def cars(self, distance, destination):
        '''We can't travel a certain distance in vehicles without fuels, so here's the fuels
        
        :param distance: The amount of distance traveled
        :type amount: int
        :param bool destinationReached: Should the fuels be refilled to cover required distance?
        :raises: :class:`RuntimeError`: Out of fuel
        
        :returns: A Car mileage
        :rtype: Cars
        '''  
        pass
```

Sphinx uses the `keyword(reserved word)`; most of the programming language does. But it is explicitly called `role` in Sphinx. In the above code, Sphinx has the `param` as a role, and `type` is a role, which is the Sphinx data type for `param`. `type` role is optional, but `param` is mandatory. The return roles document the returned object. It is different from the param role. The return role is not dependent on the` rtype` and vice-versa. The `rtype` is the type of object returned from the given function.

#### Google Style

Google Style is easier and more intuitive to use. It can be used for the shorter form of documentation. A configuration of Python file needs to be done to get started, so you need to add either `sphinx.ext.napoleon` or` sphinxcontrib.napoleon` to the extensions list in `conf.py`.

```python
class Vehicles(object):
    '''
    The Vehicle object contains a lot of vehicles
    
    Args:
        arg (str): The arg is used for...
        *args: The variable arguments are used for...
        **kwargs: The keyword arguments are used for...
        
    Attributes:
        arg (str): This is where we store arg,
    '''
    def __init__(self, arg, *args, **kwargs):
        self.arg = arg
        
    def cars(self, distance,destination):
        '''We can't travel distance in vehicles without fuels, so here is the fuels
        
        Args:
            distance (int): The amount of distance traveled
            destination (bool): Should the fuels refilled to cover the distance?
            
        Raises:
            RuntimeError: Out of fuel
            
        Returns:
            cars: A car mileage
        '''
        pass
```

#### NumPy Style

Numpy style has a lot of details in the documentation. It is more verbose than other documentation, but it is an excellent choice if you want to do detailed documentation, i.e., extensive documentation of all the functions and parameters.

```python
class Vehicles(object):
    '''
    The Vehicles object contains lots of vehicles
    
    Parameters
    ----------
    arg : str
        The arg is used for ...
    *args
        The variable arguments are used for ...
    **kwargs
        The keyword arguments are used for ...
        
    Attributes
    ----------
    arg : str
        This is where we store arg,
    '''
    def __init__(self, arg, *args, **kwargs):
        self.arg = arg
        
    def cars(self, distance, destination):
        '''We can't travel distance in vehicles without fuels, so here is the fuels
        
        Parameters
        ----------
        distance : int
            The amount of distance traveled
        destination : bool
            Should the fuels refilled to cover the distance?
            
        Raises
        ------
        RuntimeError
            Out of fuel
            
        Returns
        -------
        cars
            A car mileage
        '''
        pass
```

#### Comparison of Docstring Formats

| **Format**   | **Description**                                                                                                                                                                               | **Pros**                                                                             | **Cons**                                                                         | **Best Use Case**                                                                    |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| *Sphinx* | Uses reStructuredText for documentation, supports structured roles like `param`, `type`, `returns`, `raises`. Preferred for large projects and integrates well with Sphinx documentation. | Highly structured; Works well with Sphinx; Industry standard for large projects. | Verbose; Requires understanding reStructuredText syntax.                     | Large-scale Python projects needing structured documentation.                    |
| *Google* | Simpler and more intuitive format with `Args`, `Attributes`, `Returns`, and `Raises`. Easier to read but can be messy for multiline descriptions.                                         | Easy to read and write; Ideal for shorter documentation.                         | Multiline descriptions can get cluttered; Requires additional configuration. | General-purpose Python documentation with an easy-to-read style.                 |
| *NumPy*  | Highly detailed and structured, using `Parameters`, `Attributes`, `Returns`, `Raises`. Ideal for scientific computing and data science projects.                                          | Very detailed and suitable for complex scientific and data science projects.     | More verbose than other formats; Can be overwhelming for simple projects.    | Scientific computing and data science projects requiring detailed documentation. |
| *PyDoc*  | Python's built-in documentation tool. Can generate web pages from docstrings, and also launch a web server for interactive browsing.                                                      | Integrated with Python; Can generate web-based documentation.                    | Limited flexibility compared to other documentation tools.                   | Projects needing built-in Python documentation and web-based browsing.           |
