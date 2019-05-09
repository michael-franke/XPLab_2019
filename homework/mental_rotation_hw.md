# Homework due by Thursday May 16th (before class)

- read the "getting started guide" of the [_babe site](https://babe-project.github.io/babe_site/)
- follow the instructions to instantiate your own experiment based on the "departure point"
- create a repository for your own experiment (name it appropriately)
- change the "departure point" template as follows:
  - replace the 2-alternative forced choice task with a key-press task
  - instantiate five trials of a key-press task
  - key presses should be recorded as "same" and "different"
  - show one of the mental-rotation pictures obtainable here on each trial
  - code the key press choices as "correct" or "incorrect" based on the picture shown
  - add to the trial information (in `03_trials.js`) the following information (so that this is shown in the final output; because we might need it for analysis):
    - number of picture shown
    - degree of rotation
    - whether the picture's objects are indeed "same" or "different"
- optionally:
  - randomize the five trials using the command `_.shuffle()` from the [lodash library](https://lodash.com) which is (super useful (!) and) loaded automatically with _babe
  

