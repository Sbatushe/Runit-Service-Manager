# Runit-Service-Manager
T-ui manager for runit services

## Description
Using runit is awesome and easy. `sv start [service]` and `sv stop [service]` just works, but rsm (Runit Service Manager) is created to avoid typing NetworkManager, mysqld and friends every time you need to.

### Features:
- starting services
- stopping services

### Work in progress:
- Creating services
- Removing services

![rsm](https://github.com/Sbatushe/Runit-Service-Manager/blob/main/example.jpeg)


## Download
Clone the repository:
```
git clone https://github.com/Sbatushe/Runit-Service-Manager
```
Change permission:
```
cd Runit-Service-Manager
chmod +x rsm
```

## Configuration
rsm is just a small python3 script, thus the configuration is made via editing the source code. This is a mandatory step.
Don't worry, you need to setup just some variable before running.

1) This is your sv location, check if it's the one you're using with `which sv`, then insert it here:
```
sv = "/usr/bin/sv"
```
2) Next. Theese are your services directory. On Void Linux it's `/var/service` but could be different depending on your OS. The superuser variable is used to run `sv` commands (and not the whole script) as superuser. You should change it to `sudo` if you're using it instead of `doas`:
```
env_string = "/var/service"
superuser = "sudo"
```
3) This list is made of services which you don't want to manage with rsm. You may want to do this because usually you always need gettys, dbus, greetd and others to be always on. Having them masked is a way to declutter your interface.
```
masked = ["chronyd", "getty-tty1", "getty-tty2", "getty-tty3", "getty-tty4", "getty-tty5", "getty-tty6", "dbus", "haveged", "greetd"]
```

## Install
```
cp rsm /usr/bin/
```

## Usage
rsm is meant to be used with GUI tools such as waybar or a keyboard shortcut. To run it just call it without sudo/doas.
Once running you can:
  - move down/up with your keys
  - exit with ESC or q
  - mark for start/stop with Spacebar
  - confirm selection with Enter

