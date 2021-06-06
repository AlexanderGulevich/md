# TMUX
__---  Ctrl + b ? --- shortcuts__


#######################################################
## Sessions
#######################################################

##### start session
tmux || tmux new || tmux new -s mysession  
###### kill/delete session
tmux kill-session -t mysession
###### kill/delete session but the current
tmux kill-session -a
##### Rename session
Ctrl + b $
##### Detach from session
Ctrl + b d
##### Show all sessions
Ctrl + b s
##### Move to next session
Ctrl + b (  )

#######################################################
## Windows
#######################################################

###### Create window
Ctrl + b c
###### Rename current window
Rename current window
###### Close
Ctrl + b &
###### Previous
Ctrl + b p
##### Nex 
Ctrl + b n
##### Switch
Ctrl + b  0-9

#######################################################
## Panes
#######################################################

##### Split
Ctrl + b "
Ctrl + b %
##### Move
Ctrl + b {    }
##### Switch 
Ctrl + b     -> <- 
Ctrl + b     0-9
##### Number
Ctrl + b q
##### Pane zoom
Ctrl + b z
##### Conwert to window 
Ctrl + b !
##### Resize 
Ctrl + b  Ctrl + <-- -->
##### Close
Ctrl + b x

#######################################################
## Copy mode   (LIKE VIM)	
#######################################################
 
##### Start
Ctrl + b [
##### Scroll
Ctrl + b PgUp
##### Quite
q
##### Go to top/bottom line
g/G




