---
title: Pluggable Authentication Modules (PAM)
description: 
published: true
tags: curriculum, basic, linux
editor: markdown
---
# Introduction 


# Changing Password Settings and Configuring PAM on Ubuntu 20

In Ubuntu 20, you can change password settings and configure Pluggable Authentication Modules (PAM) to enhance security. This guide covers adjustments to password settings in `/etc/login.defs` and PAM configuration in `/etc/pam.d/`.

## Changing Password Settings in `/etc/login.defs`

1. **Open `/etc/login.defs` with `nano` as root:**

   ```
   sudo nano /etc/login.defs
   ```

2. **Use the "Where Is" search function in `nano` by pressing Ctrl + W to find the following options:
   - `PASS_MAX_DAYS`
   - `PASS_MIN_DAYS`
   - `PASS_WARN_AGE`

3. **Change the following settings as needed:**

   ```
   PASS_MAX_DAYS   90
   PASS_MIN_DAYS   7
   PASS_WARN_AGE   14
   ```

4. **Save the file and exit `nano`.**

## Configuring PAM in `/etc/pam.d/`

Before configuring PAM, ensure you have `libpam-cracklib` installed. You can use `apt-get` to install it:

```bash
sudo apt-get install libpam-cracklib
```

### `/etc/pam.d/common-password`

1. **Open `/etc/pam.d/common-password` with `nano` as root:**

   ```bash
   sudo nano /etc/pam.d/common-password
   ```

2. **Locate the line starting with "password [success=1 default=ignore] pam_unix.so..." and add the following to the end of the line:**

   ```text
   remember=5 minlen=8
   ```

   Ensure there is a space before each setting, but no spaces between the words, the equal sign (=), and the value/number.

3. **Find the line starting with "password requisite pam_cracklib.so..." and add the following to the end of the line:**

   ```text
   ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1
   ```

   Like in step 2, include spaces before each setting, but no spaces between the values, and use negative 1 (-1) for the settings. This enforces password complexity requirements.

4. **Verify that everything is correct. Errors can disrupt PAM authentication.**

5. **Save the file and exit `nano`.**

### `/etc/pam.d/common-auth`

1. **Open `/etc/pam.d/common-auth` with `nano` as root:**

   ```bash
   sudo nano /etc/pam.d/common-auth
   ```

2. **Add the following to the end of the file:**

   ```text
   auth required pam_tally2.so deny=5 onerr=fail unlock_time=1800
   ```

   As before, include spaces before each setting without spaces between the values.

3. **Verify the configuration for accuracy to prevent authentication issues.**

4. **Save the file and exit `nano`.**

