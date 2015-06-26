Ansible role for Bitlbee IRC-other chats gateway
================================================

This simple role installs and configures the Bitlbee service and
creates a user, configuring a jabber IM integration.

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
 * Use ansible-vault for passwords
 * Add support for more protocols in the user-conf.j2 template


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

        # configuration for the users file where the IM credentials go
        # these will populate the xml configuration file
        # usually created by chatting with the &bitlbee bot
        bitlbee_user: $YOUR_USER
        # this password is created with RC4 hashing
        bitlbee_pass: $THEPASS

        # I only use Jabber so I've only managed to scrip this part
        # patches welcome to configure other protocols
        jabber_handle: stefano.maffulli@jabber.newdream.net
        # as above, RC4 hash -TO BE TESTED
        jabber_pwd: $USER_PASS
        jabber_server: $JABBER.SOMEDOMAIN
        jabber_conference: $CONFERENCE.JABBER.DOMAIN

        # Jabber groupchats to join
        jabber_channels:
            - "watercooler"
            - "disintegrator"
            - "warroom"



ACKNOWLEDGMENTS
---------------

Based on the work published by Joshua Barratt https://github.com/jbarratt/
