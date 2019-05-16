# In-class exercises May 16th 2019

In today's class you are going to adapt your Mental Rotation task in a number of steps, working towards a realization of the whole experiment.

## Update your current experiment to \_babe 0.1.0

- change file `packages.json` to include:

```
"dependencies": {
  "babe-project": "~0.1.0"
}
```

- run `npm install` again
- change your view instantiations
  - where you previously had `babeViews.Intro({XYZ})`, you would now have `babeViews.view_generator('intro', {XYZ})`
  - see https://babe-project.github.io/babe-docs/01_designing_experiments/01_template_views/
- (optional) change the file names in accordance with the new departure point:
  - https://github.com/babe-project/departure-point

## Add a lag to your key-press main task

- read the documentation on life cycles:
  - https://babe-project.github.io/babe-docs/01_designing_experiments/04_lifecycles_hooks/
- realize a 1 second inter-trial pause & a 500 ms fixation cross for your key-press task

## Add a practice session

Practice is exactly like the main task, but we will use a hook to control for correctness.

- read the part about hooks on https://babe-project.github.io/babe-docs/01_designing_experiments/04_lifecycles_hooks/ 
- use the `after_response_enabled` hook to realize a check of correctness for the practice trials
- to do this, first add to the practice trials the information which answer is correct; store it in a field called `correct`, as part of each trial object
- the function given in the docs on hooks works for a forced choice task, but not for a `key_press` view because the latter has a different response function; use instead the following function:

```javascript
const check_response = function(data, next) {
    data.response_checked = false;
    $("body").on("keydown", function(e) {
        if (data.response_checked == false) {
            const keyPressed = String.fromCharCode(
                e.which
            ).toLowerCase();
            if (keyPressed == data.key1 || keyPressed == data.key2) {
                if (data[keyPressed] === data.correct) {
                    alert('Your answer is correct! Yey!');
                } else {
                    alert('Sorry, this answer is incorrect :( The correct answer was ' + data.correct);
                }
                data.response_checked = true;
                next();
            }
        }})
}
```

## Add wrapping views & instructions

- structure your experiment by adding appropriate wrapper views, for example:
  - inform your participants that now the practice starts
  - inform your participants that practice is now over and the main show starts
  - ... 
- your instructions should make participants understand the task quickly

## Include all items

- include all items (12 practice and 48 main)
- make sure that the sequence of presentation is randomized

## Check the experiment

- do the whole experiment in `debug` mode at least twice
- save the data, load it into R and check whether everything seems correct:
  - is everything of relevance recorded?
  - is trial sequence randomized?
  - is each picture presented exactly once for each participant?
  - ...
