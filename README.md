# Run Before/After Klipper G-Code Macro

This is used to be able to dinamically run macros before/after events without hardcoding them.

Example usage:

```
[include macro_run_ba.cfg]

[gcode_macro test1]
variable_after_pie: 1
gcode:
   RESPOND PREFIX="info" MSG="Running test1"

[gcode_macro test5]
variable_after_pie: 5
gcode:
   RESPOND PREFIX="info" MSG="Running test5"


[gcode_macro test2]
variable_after_pie: 2
gcode:
   RESPOND PREFIX="info" MSG="Running test2"
   
[gcode_macro test6]
variable_before_pie: 6
gcode:
   RESPOND PREFIX="info" MSG="Running test6"
   
[gcode_macro do_stuff]
gcode:
  RUN_BA EVENT=pie TYPE="before"
  
  DO SOME STUFF HERE
  
  RUN_BA EVENT=pie TYPE="after"
```

Running command DO_STUFF will result in this output

```
Running test6
Running test1
Running test2
Running test5
```
