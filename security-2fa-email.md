# 🔒 Sécurité : 2FA et Alertes e-mail

## 🔐 Activer l’authentification 2FA (Google Authenticator)
apt install libpam-google-authenticator
nano /etc/pam.d/sshd
auth required pam_google_authenticator.so
nano /etc/ssh/sshd_config
ChallengeResponseAuthentication yes
UsePAM yes
systemctl restart sshd


## 📧 Alertes e-mail avec Postfix
apt install postfix mailutils libsasl2-modules -y
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt


Générer un mot de passe d’application Gmail puis tester :
echo "Test Email from Proxmox" | mail -s "Proxmox Alert" tonEmail@gmail.com
