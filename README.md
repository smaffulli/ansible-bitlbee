Ansible role for Bitlbee IRC-other chats gateway
================================================

This simple role installs and configures the Bitlbee service.

To use it specify the variables as in the sample playbook below. To
generate the passwords you can have a BitlBee-style MD5 hash generated
by "bitlbee -x hash <password>".

The AuthMode variable can be:

 *  Open -- Accept connections from anyone, use NickServ for user
    authentication.   (default)
 *  Closed -- Require authorization (using the PASS command during
    login) before allowing the user to connect at all.
 *  Registered -- Only allow registered users to use this server; this
    disables the register- and the account command until the user identifies
    himself.

TODO
----

 * Add SSL support

Sample playbook
---------------

    - hosts: bitlbee

      roles:
        - ansible-bitlbee

      vars:
        bitlbee_pass: $PUT_YOUR_PASS_HERE
        bitlbee_oper_pass: $YOUR_OPERATOR_PASS
        bitlbee_port: $THE_PORT
        authmode: closed


ACKNOWLEDGMENTS
---------------

Based on the work published by Joshua Barratt https://github.com/jbarratt/
