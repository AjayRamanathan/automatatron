# Automatatron

Tool for creating and working with [Elementary Cellular Automaton](http://mathworld.wolfram.com/ElementaryCellularAutomaton.html).

## Examples

### Create All Possible Automaton

```python
# Print the first 10 rows of all possible automaton:
for rule in range(1,257):
  automaton = automatatron.Engine(rule)
  automaton.run(10)
  print automaton
```

### Print 50 iterations of Rule 30

```python
automaton = automatatron.Engine(30)
automaton.run(50)
print automaton
```

Prints:

```
Rule 30, 50 iterations:
                                                  #
                                                 ###
                                                ##  #
                                               ## ####
                                              ##  #   #
                                             ## #### ###
                                            ##  #    #  #
                                           ## ####  ######
                                          ##  #   ###     #
                                         ## #### ##  #   ###
                                        ##  #    # #### ##  #
                                       ## ####  ## #    # ####
                                      ##  #   ###  ##  ## #   #
                                     ## #### ##  ### ###  ## ###
                                    ##  #    # ###   #  ###  #  #
                                   ## ####  ## #  # #####  #######
                                  ##  #   ###  #### #    ###      #
                                 ## #### ##  ###    ##  ##  #    ###
                                ##  #    # ###  #  ## ### ####  ##  #
                               ## ####  ## #  ######  #   #   ### ####
                              ##  #   ###  ####     #### ### ##   #   #
                             ## #### ##  ###   #   ##    #   # # ### ###
                            ##  #    # ###  # ### ## #  ### ## # #   #  #
                           ## ####  ## #  ### #   #  ####   #  # ## ######
                          ##  #   ###  ####   ## #####   # ##### #  #     #
                         ## #### ##  ###   # ##  #    # ## #     #####   ###
                        ##  #    # ###  # ## # ####  ## #  ##   ##    # ##  #
                       ## ####  ## #  ### #  # #   ###  #### # ## #  ## # ####
                      ##  #   ###  ####   #### ## ##  ###    # #  ####  # #   #
                     ## #### ##  ###   # ##    #  # ###  #  ## ####   ### ## ###
                    ##  #    # ###  # ## # #  ##### #  ######  #   # ##   #  #  #
                   ## ####  ## #  ### #  # ####     ####     #### ## # # #########
                  ##  #   ###  ####   #### #   #   ##   #   ##    #  # # #        #
                 ## #### ##  ###   # ##    ## ### ## # ### ## #  ##### # ##      ###
                ##  #    # ###  # ## # #  ##  #   #  # #   #  ####     # # #    ##  #
               ## ####  ## #  ### #  # #### #### ##### ## #####   #   ## # ##  ## ####
              ##  #   ###  ####   #### #    #    #     #  #    # ### ##  # # ###  #   #
             ## #### ##  ###   # ##    ##  ###  ###   ######  ## #   # ### # #  #### ###
            ##  #    # ###  # ## # #  ## ###  ###  # ##     ###  ## ## #   # ####    #  #
           ## ####  ## #  ### #  # ####  #  ###  ### # #   ##  ###  #  ## ## #   #  ######
          ##  #   ###  ####   #### #   ######  ###   # ## ## ###  ######  #  ## #####     #
         ## #### ##  ###   # ##    ## ##     ###  # ## #  #  #  ###     ######  #    #   ###
        ##  #    # ###  # ## # #  ##  # #   ##  ### #  ##########  #   ##     ####  ### ##  #
       ## ####  ## #  ### #  # #### ### ## ## ###   ####         #### ## #   ##   ###   # ####
      ##  #   ###  ####   #### #    #   #  #  #  # ##   #       ##    #  ## ## # ##  # ## #   #
     ## #### ##  ###   # ##    ##  ### ########### # # ###     ## #  #####  #  # # ### #  ## ###
    ##  #    # ###  # ## # #  ## ###   #           # # #  #   ##  ####    ###### # #   ####  #  #
   ## ####  ## #  ### #  # ####  #  # ###         ## # ##### ## ###   #  ##      # ## ##   #######
  ##  #   ###  ####   #### #   ###### #  #       ##  # #     #  #  # ##### #    ## #  # # ##      #
 ## #### ##  ###   # ##    ## ##      #####     ## ### ##   ######## #     ##  ##  #### # # #    ###
##  #    # ###  # ## # #  ##  # #    ##    #   ##  #   # # ##        ##   ## ### ###    # # ##  ##  #
```

## Custom row handler

```python
def row_handler(row):
  print row

# Run the next 10 iterations, and pass results into specified handler.
automaton.run(10, handler=row_handler)
```

## Stream Center of Output into Function

```python
automaton = automatatron.Engine(30)
def stream_handler(row, _):
  print automatatron.default_string_formatter(row)
  time.sleep(0.05)
automaton.stream(stream_handler, width=101)
```

Streams continuously to stdout:

```
                                                 ###
                                                ##  #
                                               ## ####
                                              ##  #   #
                                             ## #### ###
                                            ##  #    #  #
                                           ## ####  ######
                                          ##  #   ###     #
                                         ## #### ##  #   ###
                                        ##  #    # #### ##  #
                                       ## ####  ## #    # ####
                                      ##  #   ###  ##  ## #   #
                                     ## #### ##  ### ###  ## ###
                                    ##  #    # ###   #  ###  #  #
                                   ## ####  ## #  # #####  #######
                                  ##  #   ###  #### #    ###      #
                                 ## #### ##  ###    ##  ##  #    ###
                                ##  #    # ###  #  ## ### ####  ##  #
                               ## ####  ## #  ######  #   #   ### ####
                              ##  #   ###  ####     #### ### ##   #   #
                             ## #### ##  ###   #   ##    #   # # ### ###
                            ##  #    # ###  # ### ## #  ### ## # #   #  #
                           ## ####  ## #  ### #   #  ####   #  # ## ######
                          ##  #   ###  ####   ## #####   # ##### #  #     #
                         ## #### ##  ###   # ##  #    # ## #     #####   ###
                        ##  #    # ###  # ## # ####  ## #  ##   ##    # ##  #
                       ## ####  ## #  ### #  # #   ###  #### # ## #  ## # ####
                      ##  #   ###  ####   #### ## ##  ###    # #  ####  # #   #
                     ## #### ##  ###   # ##    #  # ###  #  ## ####   ### ## ###
                    ##  #    # ###  # ## # #  ##### #  ######  #   # ##   #  #  #
                   ## ####  ## #  ### #  # ####     ####     #### ## # # #########
                  ##  #   ###  ####   #### #   #   ##   #   ##    #  # # #        #
                 ## #### ##  ###   # ##    ## ### ## # ### ## #  ##### # ##      ###
                ##  #    # ###  # ## # #  ##  #   #  # #   #  ####     # # #    ##  #
               ## ####  ## #  ### #  # #### #### ##### ## #####   #   ## # ##  ## ####
              ##  #   ###  ####   #### #    #    #     #  #    # ### ##  # # ###  #   #
             ## #### ##  ###   # ##    ##  ###  ###   ######  ## #   # ### # #  #### ###
            ##  #    # ###  # ## # #  ## ###  ###  # ##     ###  ## ## #   # ####    #  #
           ## ####  ## #  ### #  # ####  #  ###  ### # #   ##  ###  #  ## ## #   #  ######
          ##  #   ###  ####   #### #   ######  ###   # ## ## ###  ######  #  ## #####     #
         ## #### ##  ###   # ##    ## ##     ###  # ## #  #  #  ###     ######  #    #   ###
        ##  #    # ###  # ## # #  ##  # #   ##  ### #  ##########  #   ##     ####  ### ##  #
       ## ####  ## #  ### #  # #### ### ## ## ###   ####         #### ## #   ##   ###   # ####
      ##  #   ###  ####   #### #    #   #  #  #  # ##   #       ##    #  ## ## # ##  # ## #   #
     ## #### ##  ###   # ##    ##  ### ########### # # ###     ## #  #####  #  # # ### #  ## ###
    ##  #    # ###  # ## # #  ## ###   #           # # #  #   ##  ####    ###### # #   ####  #  #
   ## ####  ## #  ### #  # ####  #  # ###         ## # ##### ## ###   #  ##      # ## ##   #######
  ##  #   ###  ####   #### #   ###### #  #       ##  # #     #  #  # ##### #    ## #  # # ##      #
 ## #### ##  ###   # ##    ## ##      #####     ## ### ##   ######## #     ##  ##  #### # # #    ###
##  #    # ###  # ## # #  ##  # #    ##    #   ##  #   # # ##        ##   ## ### ###    # # ##  ##  #
# ####  ## #  ### #  # #### ### ##  ## #  ### ## #### ## # # #      ## # ##  #   #  #  ## # # ### ###
  #   ###  ####   #### #    #   # ###  ####   #  #    #  # # ##    ##  # # #### ########  # # #   #
#### ##  ###   # ##    ##  ### ## #  ###   # ######  ##### # # #  ## ### # #    #       ### # ## ###
#    # ###  # ## # #  ## ###   #  ####  # ## #     ###     # # ####  #   # ##  ###     ##   # #  #
##  ## #  ### #  # ####  #  # #####   ### #  ##   ##  #   ## # #   #### ## # ###  #   ## # ## ##### #
  ###  ####   #### #   ###### #    # ##   #### # ## #### ##  # ## ##    #  # #  #### ##  # #  #     #
 ##  ###   # ##    ## ##      ##  ## # # ##    # #  #    # ### #  # #  ##### ####    # ### #####   ##
 # ###  # ## # #  ##  # #    ## ###  # # # #  ## #####  ## #   #### ####     #   #  ## #   #    # ##
## #  ### #  # #### ### ##  ##  #  ### # # ####  #    ###  ## ##    #   #   ### #####  ## ###  ## # #
#  ####   #### #    #   # ### ######   # # #   ####  ##  ###  # #  ### ### ##   #    ###  #  ###  # #
 ###   # ##    ##  ### ## #   #     # ## # ## ##   ### ###  ### ####   #   # # ###  ##  ######  ### #
##  # ## # #  ## ###   #  ## ###   ## #  # #  # # ##   #  ###   #   # ### ## # #  ### ###     ###   #
  ### #  # ####  #  # #####  #  # ##  #### #### # # # #####  # ### ## #   #  # ####   #  #   ##  # ##
###   #### #   ###### #    ###### # ###    #    # # # #    ### #   #  ## ##### #   # ###### ## ### #
   # ##    ## ##      ##  ##      # #  #  ###  ## # # ##  ##   ## #####  #     ## ## #      #  #   ##
# ## # #  ##  # #    ## ### #    ## #######  ###  # # # ### # ##  #    ####   ##  #  ##    ###### ##
# #  # #### ### ##  ##  #   ##  ##  #      ###  ### # # #   # # ####  ##   # ## ###### #  ##      #
  #### #    #   # ### #### ## ### ####    ##  ###   # # ## ## # #   ### # ## #  #      #### #    ####
 ##    ##  ### ## #   #    #  #   #   #  ## ###  # ## # #  #  # ## ##   # #  #####    ##    ##  ##
 # #  ## ###   #  ## ###  ###### ### #####  #  ### #  # ####### #  # # ## ####    #  ## #  ## ### #
 # ####  #  # #####  #  ###      #   #    ######   #### #       #### # #  #   #  #####  ####  #   ##
## #   ###### #    ######  #    ### ###  ##     # ##    ##     ##    # ##### #####    ###   #### ##
   ## ##      ##  ##     ####  ##   #  ### #   ## # #  ## #   ## #  ## #     #    #  ##  # ##    # ##
  ##  # #    ## ### #   ##   ### # #####   ## ##  # ####  ## ##  ####  ##   ###  ##### ### # #  ## #
### ### ##  ##  #   ## ## # ##   # #    # ##  # ### #   ###  # ###   ### # ##  ###     #   # ####  ##
    #   # ### #### ##  #  # # # ## ##  ## # ### #   ## ##  ### #  # ##   # # ###  #   ### ## #   ###
#  ### ## #   #    # ###### # # #  # ###  # #   ## ##  # ###   #### # # ## # #  #### ##   #  ## ##  #
 ###   #  ## ###  ## #      # # #### #  ### ## ##  # ### #  # ##    # # #  # ####    # # #####  # ###
 #  # #####  #  ###  ##    ## # #    ####   #  # ### #   #### # #  ## # #### #   #  ## # #    ### #
##### #    ######  ### #  ##  # ##  ##   # ##### #   ## ##    # ####  # #    ## #####  # ##  ##   ###
      ##  ##     ###   #### ### # ### # ## #     ## ##  # #  ## #   ### ##  ##  #    ### # ### # ##
#    ## ### #   ##  # ##    #   # #   # #  ##   ##  # ### ####  ## ##   # ### ####  ##   # #   # # #
...
```