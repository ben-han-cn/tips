# Verbs
- d
- D # delete from current pos to end of line
- c
- C # change from current pos to end of line
- y
- Y # yank one line
- >
- <
- . # repeat last action

# Preposition (used with verbs)
- i # inside
- a # around

# Move
- h,j,k,l
- w,e,b
- W,E,B(ignore all non-whitespace character including '-',',' etc) 
- 0
- $ 
- ( # begin of sentence
- ) # end of sentence

# Search
- /regex  # search next instance
- n
- N
- t
- T
- f
- F

# Block view mode inserting
ctrl-v into block mode (the cursor place will be the insert place)
select the lines wants to insert
shift-i into insert mode, then insert what you want
use esc come back to normal mode 
