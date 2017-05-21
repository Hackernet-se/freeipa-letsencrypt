How to use Let's encrypt certificates with FreeIPA WebUI.

Prerequisite:
* Backup /etc/httpd/alias.
* clone this repository and cd into it.
* Import the certificates.
  * `ipa-cacert-manage install "DSTRootCAX3.pem" -n DSTRootCAX3 -t C,,`
  * `ipa-cacert-manage install "LetsEncryptAuthorityX3.pem" -n letsencryptx3 -t C,,`
* Update certificates `ipa-certupdate`


After you have imported root certificates you are able to import the signed certificates you goten.
* `ipa-server-certinstall -w fullchain.pem privkey.pem`
* Restart httpd service and dirsrv.
* `systemctl restart dirsrv@REALM.service`
* `systemctl restart httpd.service`

For more tutorials visit https://hackernet.se 