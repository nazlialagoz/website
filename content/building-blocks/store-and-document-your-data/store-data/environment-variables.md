---
title: "Configure Environment Variables"
description: "This block explains how to list contents, download content from and upload content to a AWS S3 bucket."
keywords: "environment variables"
date: 2021-02-17
weight: 3
author: "Roy Klaasse Bos"
authorlink: "https://www.tilburguniversity.edu/staff/r-j-klaassebos"
aliases:
  - "/use/aws-s3"
---

## Overview <!-- Goal of the Building Block -->
When working with APIs or cloud services, you usually need to access some personal credentials or secret keys. With environment variables we can access such variables without literally writing them down in a notebook or script (e.g., `password = "..."`). The basic idea is that these global variables are stored permanently and are attached to your operating system. Therefore, you can access these variables regardless of whether you are working in RStudio or a Jupyter Notebook.

As long as you never print its value, you can safely push a script that references a environment variable to a public Github repository without having to worry about disclosing any login credentials. However, you do need to inform others with whom you're collaborating about its value because it's not contained in the script itself.

{{% warning %}}
Never ever upload a script that contains privacy sensitive information to Github. Even if you'd remove it afterwards, it still remains visible through the repository history.  
{{% /warning %}}


## Configure Environment Variables

### Mac/Linux
1. Go to the terminal and type `printenv` to list all environment variables stored on your machine. 
2. Open the terminal, go to your user directory (shortcut: `cd ~`), and type `nano .bash_profile` to open a text editor in the terminal. 
3. Within this window you can create new variables as follows: `export [VARIABLE_NAME]="the string value you want to store";`. Note that there is no space between the variable name and its value and that the string is enclosed in double quotes. 
4. Exit the editor by pressing Ctrl + X, choose `Y` (to save changes), and finally press `Enter`. 
5. You can check whether everything worked out correctly by restarting your terminal and typing `printenv` (`VARIABLE_NAME` should be listered there now!). If the new envirionment variables didn't show up, you may need to use `nano .zshrc` instead of `nano .bash_profile` (see step 2).

### Windows
1. Open up "Control Panel" > "System and Security" > "System".
2. In the left sidebar click on "Advanced system settings".
3. Click on "Environment Variables" in the bottom right.
4. Create a new "User Variable" (top list) and fill out the "Variable name" and "Variable value".
5. Double click "OK" twice.


## Access Environment Variables
After you have imported the `os` (or `Sys`) library, you can easily assign the value of the environment variable (`VARIABLE_NAME`) to a variable. Subsequently, you can re-use the variable throughout the script, for example for API authentication purposes.

{{% codeblock %}}

```python
import os
# VARIABLE_NAME is the name of the environment variable you defined in the terminal 
api_password = os.environ['VARIABLE_NAME']   
```

```R
library(Sys)
# VARIABLE_NAME is the name of the environment variable you defined in the terminal 
api_password = Sys.getenv(c("VARIABLE_NAME"))
```


{{% /codeblock %}}



## See also

- [Mac/Linux tutorial](https://www.youtube.com/watch?v=5iWhQWVXosU)
- [Windows tutorial](https://www.youtube.com/watch?v=IolxqkL7cD8)
