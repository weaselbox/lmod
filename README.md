# lmod

A perl script for modifying existing LDAP entries.  Because ldapmodify sucks.

## Features

- Interactive mode
- Oneliner mode
- Supports standard LDAP filters.
- TLS used if supported by server.
- Automatic selection of rc file based on host arg, falls back to default rc file, or prompts if no rc files are present.

## Usage

`lmod [-h host][-b searchbase][filter][operation][attribute][value]`

Where *filter* is a valid key=value LDAP filter. (complex filters allowed) and operation is *add*, *rep* (replace), or *del* (delete).  If insufficient arguments are provided interactive mode will be used.

## rcfile Format

    LDAPHOST:ldap.example.com
    LDAPBASE:dc=example,dc=com
    BINDDN:uid=some_dude,ou=people,dc=example,dc=com
    BINDPASS:pa55w0rd!

If BINDDN and/or BINDPASS are missing, the user will be prompted for credentials.

## Notes

Certificate verification is disabled in TLS mode in the assumption self-signed certs are probably being used.

While this script can be used to add/delete/replace any attribute, it has no awareness of those attributes. If used for passwords those passwords will appear in clear text.
