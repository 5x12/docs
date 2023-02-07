

# Intro

Imagine you have a file `code.py` with the following functions: 

```python 
def print_hello(name):
    print(f"Hello {name}!")

def print_bye(name):
    print(f"Bye {name}!")

def add_to_editor():
    data = {'x': [0.25, 0.60, 0.71, 1.20, 1.75, 2.26, 2.50, 2.50, 2.88, 2.91], 
        'y': [1.41, 0.39, 1.29, 2.30, 0.59, 1.70, 1.35, 2.90, 0.61, 2.00],
        'target': ['blue', 'blue', 'blue', 'blue', 'blue', 'green', 'green', 'green', 'green', 'green']
           }  
    df = pd.DataFrame(data)  
    df.to_csv('/Users/andrewwolf/rrrrrrrr.csv')

if __name__ == "main":
    print_hello("Ben")
    print_bye("Alex")
    add_to_editor()
```

You can now run the script by executing the following from the Terminal:

```
python3 code.py
>> Hello Ben
>> Bye Alex
```


As you can see, the ETL pipeline runs and finishes without any errors. But what if you want to run the pipeline at a schedule? That’s where Prefect comes in.


# Prefect Intro


Let’s start with the most simple one — tasks. It’s basically a single step of your workflow. To follow along, create a new Python file called task_code.py. Copy everything from code.py, and you’re ready to go.


To convert a Python function to a Prefect Task, you first need to make the necessary import — from prefect import task, and decorate any function of interest. Here’s an example:


```python 
from prefect import task


@task
def print_hello(name):
    print(f"Hello {name}!")

@task
def print_buy(name):
    print(f"Buy {name}!")

@task
def add_to_editor():
    data = {'x': [0.25, 0.60, 0.71, 1.20, 1.75, 2.26, 2.50, 2.50, 2.88, 2.91], 
        'y': [1.41, 0.39, 1.29, 2.30, 0.59, 1.70, 1.35, 2.90, 0.61, 2.00],
        'target': ['blue', 'blue', 'blue', 'blue', 'blue', 'green', 'green', 'green', 'green', 'green']
       }  

    df = pd.DataFrame(data)  

    df.to_csv('/Users/andrewwolf/rrrrrrrr.csv')
```





