# Resetting Passwords

## If you're logged in as Admin user

- Open `Computer Management` -> `Local Users and Groups` -> `Users`
- Right click on a user and choose `Set Password`
- You can disable any users that you are unfamiliar with
  - Don't delete them in case they are needed for scripts, programs, etc.

## If you're not logged in

- [Sticky Keys Hack](https://fossbytes.com/sticky-key-feature-and-reset-windows-password-using-cmd/)
  - Boot into a live OS, mount thje Windows filesystem, and change the program that 5 shifts is bound to from Sticky Keys to `cmd.exe`
- Use [chntpw](https://en.wikipedia.org/wiki/Chntpw) to overwrite the [SAM](https://en.wikipedia.org/wiki/Security_Account_Manager) database
