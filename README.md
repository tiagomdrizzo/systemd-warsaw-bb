# systemd-warsaw-bb

This is a systemd service configuration file for Banco do Brasil warsaw process, but you can change to whatever you want (obviously).
You're in this repository, so I'm confident you know what we are talking about (I'm looking at you Banco do Brasil).

- Tested on Fedora 26.

- **Prerequisites**:
  - Before starting, check if the "security module" is already installed in your system, and if not make to follow the internet bank installation process to the 'T'.
  - Hint: you will probably have issues to install the "security module" under Wayland (use X environment).
  - You might need to change the "security module" script location for `ExecStart` and/or `ExecStop` depending on your system.
  - SELinux is set to enforce mode.

- **Installation**:
  - Copy `warsaw-bb.service` file to `/etc/systemd/system/warsaw-bb.service`
  - Set the owner:group to root and permission 644:
  ~~~
  # chown root: /etc/systemd/system/warsaw-bb.service
  # chmod 644 /etc/systemd/system/warsaw-bb.service
  ~~~
  - Add SELinux context `systemd_unit_file_t` to the file. This is the default for `/etc/systemd/system/` directory, so the command below will do the trick
   ~~~
   # restorecon -RFvvv /etc/systemd/system/warsaw-bb.service
   ~~~
  - Reload systemd daemon:
  ~~~
  # systemctl daemon-reload
  ~~~
  - Try checking if `warsaw-bb.service` is now being displayed:
  ~~~
  # systemctl status warsaw-bb.service
  ~~~
  - Enable/start it as needed.
