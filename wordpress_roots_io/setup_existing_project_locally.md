# Setup an existing https://roots.io project locally

1. Clone the repository.
2. Retrieve `.vault_pass` & `.env` files. Make sure to add them to the `trellis/` and `site/` directories respectively.
3. Setup Bedrock by running `composer install` in `site/`.
4. Setup Sage by running `composer install` and `yarn` in `site/web/app/themes/<theme name>/`.
5. Fire up Trellis by running `vagrant up` in `trellis/`.
6. Connect to the VM using `vagrant ssh` and navigate to the `/srv/www/<theme name>/current/` directory. This is where we import the database.
7. In order to provision and/or deploy an ansible project, it is necessary that your public SSH keys be added to the `authorized_key` files for both the `web` and `admin` users on the server.
8. SSH into the machine `ssh web@<remote url>:/srv/www/<theme name>/current/` and run a `wp db export`. You might want to add `--exclude_tables=users`.
9. Copy the database from the remote server to your local directory using `scp <user>@<remote url>:/srv/www/<theme neme>current/<filename>.sql <target directory>`.
10. Run `wp db import` from your local Sage directory.


Note: During server provisioning, the `admin` user will be created with the value of `admin_user` inside `trellis/group_vars/all/users.yml`.
