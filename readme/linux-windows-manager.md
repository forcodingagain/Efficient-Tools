# Linux windows manager

## 1.Screen

### 1.1 session resume

```bash
screen -r
```

### 1.2 Multi-window

### 1.3 session sharing

### 1.4 Common command tutorial

#### 1.4.1 Create a new screen session

```bash
screen -S <session name>
```

#### 1.4.2 Exit the current screen session

```bash
ctrl+a  d
```

#### 1.4.3 View all screen sessions

```bash
screen -ls
```

#### 1.4.4 Enter (resume) a screen session

```bash
screen -r <session id>
```

#### 1.4.5 close screen session

```bash
screen -X -S <session id> quit
```

#### 1.4.6 detach a session

```
screen -d <session name>
```

#### 1.4.7 detach a session and return to a session

```
screen -d -r <session name>
```

#### 1.4.8 Detach a session to log out and return to a session

```
screen -D -r <session name>
```

### 1.5 hot key

#### 1.5.1 create a new window

```bash
ctrl+a  c
```

#### 1.5.2 switch to next window

```bash
ctrl+a  n
```

#### 1.5.3 switch to next window

```bash
ctrl+a  p
```

#### 1.5.4 close current window

```bash
ctrl+a  k
ctrl+a  x
```

#### 1.5.5 create split screen up and down

```
ctrl+a  shift+s
```

#### 1.5.6 switch window

```
ctrl+a  tab
```

#### 1.5.7 create a vertical split window

```
ctrl+a |
```

#### 1.5.8 other commands

```bash
Ctrl+a+?：显示所有键绑定信息
Ctrl+a+c：创建一个新的运行shell窗口并切换到该窗口
Ctrl+a+n：切换到下一个window
Ctrl+a+p：切换到前一个window
Ctrl+a+0..9：切换到第 0..9 个window
Ctrl+a [Space]：由视窗0循序切换到视窗9 
Ctrl+a+d：分离当前screen会话，即退出当前screen会话。将目前的screen session (可能含有多个 windows) 丢到后台执行，并会回到还没进 screen 时的状态，此时在 screen session 里，每个 window 内运行的 process (无论是前台/后台)都在继续执行，即使 logout 也不影响。Ctrl+a+z -> 把当前session放到后台执行，用 shell 的 fg 命令则可回去。
Ctrl+a Ctrl+a：在两个最近使用的window间切换。
Ctrl+a+x：锁住当前的window，需用用户密码解锁。
Ctrl+a+w：显示所有窗口列表。
Ctrl+a+t：time，显示当前时间和系统的平均负载（Load Average，是一段时间内系统的平均负载，这个一段时间一般取1分钟、5分钟、15分钟）。
Ctrl+a+k：kill window，强行关闭当前的window
Ctrl+a+[：进入copy mode，在copy mode下可以回滚、搜索、复制就像使用vi一样，常用快捷键有： 
 Ctrl+b：Backward，PageUp
 Ctrl+f：Forward，PageDown 
 H：High，将光标移至左上角
 L：Low，将光标移至左下角
 0：移到行首
 $：行末
 w：forward one word，以字为单位往前移
 b：backward one word，以字为单位往后移
 Space：第一次按为标记区起点，第二次按为终点
 Esc 结束copy mode
Ctrl+a+]：paste，把刚刚在 copy mode 选定的内容贴上。sh
```





## 2.Tmux

## 3.Byobu
