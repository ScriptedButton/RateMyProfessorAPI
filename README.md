# RateMyProfessorAPI


## Setup
**Please note that this has only been tested on Python 3.9.1. If this doesn't work for older versions, open up an Issue.**

Install the package using the following command:
```
python -m pip install RateMyProfessorAPI 
```

To update the package, use the following command:
```
python -m pip install RateMyProfessorAPI --upgrade
```

To use the package in your program, please import the package:
```py
import ratemyprofessor
```

## Uninstallation
To uninstall the package, use the following command:
```
python -m pip uninstall RateMyProfessorAPI
```

## Usage
As of version 1.0.0, there are limited ways to retrieve professor ratings. 
Only ratings, difficulty ratings, and names can be displayed at this time.

To retrieve a list of professors, you have to first specify the school:
```python
ratemyprofessor.get_school_by_name("School Name here")
```
This will return `None` if no school is found corresponding with that name. 
Alternatively, to search for multiple schools, use
```python
ratemyprofessor.get_schools_by_name("School Name here")
```
This will return a list of `School`s.

Using the `School` object obtained from the previous commands, you can use that to find the professor:
```python
ratemyprofessor.get_professor_by_school_and_name(school, "Professor Name") 
```
where school refers to a `School` object.
Alternatively, to search for multiple professors, use
```python
ratemyprofessor.get_professor_by_schools_and_name(school, "Professor Name") 
```
This will return a list of `Professor`s.

Each `Professor` object has a `rating`, `difficulty`, `id`, `name`, `department`, and `would_take_again`.
Note that some of these will be `None`, like `would_take_again`.

Each `School` object has a `id` and `name`.

## Example
```python
import ratemyprofessor

professor = ratemyprofessor.get_professor_by_school_and_name(
    ratemyprofessor.get_school_by_name("Case Western Reserve University"), "Connamacher")
if professor is not None:
    print(f"{professor.name} works in the {professor.department} Department of {professor.school.name}.")
    print(f"Rating: {professor.rating} / 5.0")
    print(f"Difficulty: {professor.difficulty} / 5.0")
    print(f"Total Ratings: {professor.num_ratings}")
    if professor.would_take_again is not None:
        print(f"Would Take Again: {round(professor.would_take_again, 1)}%")
    else:
        print("Would Take Again: N/A")

```

**Output:**
```
Harold Connamacher works in the Computer Science Department of Case Western Reserve University.
Rating: 4.7 / 5.0
Difficulty: 3.8 / 5.0
Total Ratings: 102
Would Take Again: 86.2%
```
See `examples` for more examples.

## Acknowledgements and License
This can be seen as a continuation of the [RateMyProfessorPyAPI](https://pypi.org/project/RateMyProfessorPyAPI/) project that can also be found on GitHub [here](https://github.com/remiliacn/RateMyProfessorPy).
This serves as an inspiration for this project.
This project is also licensed under the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0). See LICENSE for more details.