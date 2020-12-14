
## SETUP

1) change your git information (name, email) in vars/git.yml
    before running.

2) create more secure users than the defaults provided.
    a) create a users.yml file.

        EXAMPLE:
            ---
            users:
                - name: "regular-joe"
                  sudoer: no
                  password: $6$gfRmzdOBCvK$v2Vwwx5sPkLY15uIIhr4fbn7nkhn0R6aZvuivMN2RIepgPuUnf2vRTarYEDVWhPNSxoxpnpSloVkBRVin7qau0
                  ...
        
        You can also look at vars/default-users.yml for an example.
        If you do not create or use a users.yml file,
         vars/default-users.yml will be used.
        Default accounts created by vars/default-users.yml:
            - user: admin
              sudoer: yes
              password: password
            - user: regular
              sudoer: no
              password: password
        Generate new password hashes using
            > mkpassword --method=SHA-512

    b) under your calling playbook, include your users.yml

        include_vars:
            - "users.yml"
            ...
        include_roles:
            - tpboyle.setup
            ...
