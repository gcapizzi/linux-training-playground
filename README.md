# linux-training-playground
A Vagrant-based playground for the [_System Programming for Linux Containers_ training](http://man7.org/training/sys_prog_lxcon/index.html) 🐧

## Starting the VM

You will need:
* [Virtualbox](https://www.virtualbox.org/)
* [Vagrant](https://www.vagrantup.com/)

To get the VM running:
```
$ vagrant up
```

## Working with the VM

Like every Vagrant project, this playground is set up to let you use your own editing environment. To achieve this, the playground folder is mounted in the VM, under `/vagrant`. This allows you to edit your files using your favourite editor, and then compile them on the VM.

## Accessing the GRUB boot prompt

Some exercises will require to boot Linux with different boot parameters. To do this, you'll need access the GRUB prompt. For this reason, this VM starts with a GUI.

## Stopping the VM

```
vagrant halt
```

## Destroying the VM

```
vagrant destroy
```
