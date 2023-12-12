sshd_configured
===============

Applies basic configuration and hardening to OpenSSH.

Role Variables
--------------

defaults/main.yaml:

    sshd_port: 2211
    sshd_address_family: "inet"
    sshd_listen_address: "0.0.0.0"
    sshd_login_grace_time: "30s"
    sshd_max_auth_tries: 3
    sshd_max_sessions: 10
    sshd_authentication_methods: "publickey"
    sshd_password_auth: "no"
    sshd_agent_forwarding: "no"
    sshd_tcp_forwarding: "yes"
    sshd_permit_user_environment: "no"
    sshd_log_level: "VERBOSE"
    sshd_log_facility: "AUTH"
    sshd_kex_algo: "curve25519-sha256@libssh.org,ecdh-sha2-nistp521,ecdh-sha2-nistp384,ecdh-sha2-nistp256,diffie-hellman-group-exchange-sha256"
    sshd_ciphers: "chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com,aes256-ctr,aes192-ctr,aes128-ctr"
    sshd_macs: "hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-512,hmac-sha2-256,umac-128@openssh.com"
    sshd_moduli_file: "/etc/ssh/moduli"
    sshd_moduli_min: 3071

Example Playbook
----------------

    - hosts: all
      become: yes
      roles:
      - { role: 'nett-ef.sshd_configured', tags: sshd, sshd_port: 2200 }

Platforms
---------

    - name: Ubuntu
      versions:
        - kinetic
        - lunar
        - mantic
 
Requirements
------------

None

Dependencies
------------

None

License
-------

MIT

Author Information
------------------

Copyright (c) 2023 Fedor Saveliev (https://github.com/nett-ef)

The role was copied from my playbook (https://github.com/nett-ef/testbox) to use separately.
