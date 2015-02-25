# Zabbix template for Mikrotik router

This is Zabbix template for Mikrotik router that use SNMP and Low Level Discovery for network interfaces.

![Lates data example](https://cloud.githubusercontent.com/assets/2463895/6367797/39e369e2-bcdf-11e4-840b-11df09a0e887.png)

## How to use

### SNMP

Enable SNMP in you Mikrotik router. Set SNMP-community to ``public``. If you want to use another word for community **you have to change it in the template's items**. Or create appropriate {MACRO}.

### Value mapping

This template uses some value mapping. Please create the following in ``Administration -> General -> Value mapping``:

- Network port status, [1 ⇒ Up, 2 ⇒ Down].
- Network port admin status, [1 ⇒ Enabled, 2 ⇒ Disabled]

Like this:

![Value mapping](https://cloud.githubusercontent.com/assets/2463895/6367773/fa051514-bcde-11e4-99bd-3bb381b38093.png)

If you don't want to use value mapping, please delete all th lines with:

                            <valuemap>
                                <name>Network port admin status</name>
                            </valuemap>

and

                            <valuemap>
                                <name>Network port status</name>
                            </valuemap>

### Regular expression

This template uses Low Level Discovery for network interfaces. To filter unactive interfaces it uses regular expression. Please, create the following in ``Administration -> General -> Regular expression``:

- Mikrotik interfaces	1	, 	``.*slave.*``	[Result is FALSE]

Like this:

![Regular expression](https://cloud.githubusercontent.com/assets/2463895/6368063/ca544670-bce1-11e4-983d-ce6c6637fb8d.png)

If you don't want to use special regular expression you will have to change or remove it in the LLD rule filter tab:

![LLD filter](https://cloud.githubusercontent.com/assets/2463895/6367771/fa03cf4c-bcde-11e4-87ad-366ba809a32e.png)

### Import template

Import template in Zabbix frontend: ``Configurtaion -> Template -> Import``.

Add the template to the mikrotik host. Be sure to set **SNMP IP-address** and **Agent interfaces IP-address** (used for ping).

You can find [more screenshots here](https://github.com/YSmetana/zabbix-mikrotik-snmp/issues/1).

Enjoy! ;)
