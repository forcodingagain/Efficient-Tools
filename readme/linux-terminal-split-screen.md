# Linux Terminal Split Screen

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

## 2.Tmux

## 3.Byobu
