# tmux commands

* list sessions

```
tmux ls
```

* attach to a session

```
tmux attach -t session_name
```

* detach from session

```
<leader> d
```

* close or kill pane

```
<leader> x
```

* resize pane
```
^B :resize-p -D 2
^B :resize-p -U 2
^B :resize-p -L 2
^B :resize-p -R 2
```