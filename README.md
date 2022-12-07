<a name="readme-top"></a>

<!-- [![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url] -->
[![MIT License][license-shield]][license-url]
<!-- [![LinkedIn][linkedin-shield]][linkedin-url] -->



<br />
<div align="center">

  <h3 align="center">Tiny Data Analytics Tool</h3>

  <p align="center">
    A tiny data analytics tool from when I started learning Python
    <br />
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#license">License</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

This is a tiny Data Analytics Tool from when started learning Python in 2019. I don't maintain it and decided primarily to publish it for a friend of mine, who needed such “tiny” tool for his local Data Analytics Scripts. An Example of how to use is provided below under the `Getting Started` section.

That said... This is a tiny tool encompassing a GUI for flexibly organizing Data Analytics related tasks/functions and adding custom User Input Fields if needed. It builds up a Tkinter GUI where custom functions can be started and if needed provide User Input. It can plainly execute some logic or render Matplotlib Graphs.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With

[![Python][Python]][Python-url]


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started
```python

import pandas as pd
from TinyDataAnalyticsTool import TinyDataAnalyticsTool
import matplotlib.pyplot as plt
import matplotlib
matplotlib.use("TkAgg")

def myFunc(*args, **kwargs):
    # Nested dictionary of User Input including Tkinter Objects for further manipulations if required
    user_inputs : dict = kwargs.get('user_inputs') 
    # Trimmed only if User did NOT select option 'All' 
    trimmed_data_based_on_user_input :pd.DataFrame = kwargs.get('data') 
    print(user_inputs)
    print(trimmed_data_based_on_user_input)
    plt.hist(trimmed_data_based_on_user_input["Column1"])
    plt.show()

def main():                      
    #Import: Use the function name (e.g. myFunc) consistent 

    # Read your Data as Pandas Data Frame
    data = pd.DataFrame({'Column1': [1,2,3,4,5],'Column2':[5,4,3,2,1]})

    #Here you give as parameter your Data
    dict_data = {'myFunc' : data}

    #Here you specify the function which shall be called in the Analytics Class above
    func_dict = {"myFunc" : myFunc}

    #Here you specify special options for your DropDown menu, for example if the analysis should be based on relative or absoloute values
    #You can pass multiple special dicts in form of a nested dict
    dict_special_dropdown_options = {'myFunc' : {'Method (Parameters to choose from as a User not in dataset)' : ['Mean' , 'Median', 'Standarddeviation']}}

    #Here you specify Parameters which correspond to the column names in the dataFrame
    option_parameters_from_dataset_columns = {"myFunc" : ['Column1', 'Column2']}

    #here you can change the name of the column names for aesthetic reasons.
    func_parameters_desc = {"myFunc" : {'Column1' : 'Choice 1', 'Column2' : 'Choice 2'}}
    
    #Create the Gui and insert the parameters
    TinyDataAnalyticsTool(func_dict, option_parameters_from_dataset_columns, dict_data = dict_data,
            func_parameters_display_descr=func_parameters_desc,
            dict_special_dropdown_options=dict_special_dropdown_options)

if __name__ == '__main__':
    main()
```

### Prerequisites

Python >=3.6


### Installation


pip install TinyDataAnalyticsTool

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

