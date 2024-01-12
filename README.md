# ansible_role_acme

Ansible role to manage acme certificate, use example in playbook directory to configure the generation of certificates 
Configure your acme_certificate_dir
```
#Certificate Directory
acme_certificate_dir: acme_certificate
```
and select only one acme_method dns-01 or http-01

## Example with Let's Encrypt
```
ansible-playbook -e @acme_configuration/lets-encrypt-staging.yml acme.yml
```

## Example with ZeroSSL
```
ansible-playbook -e @acme_configuration/zero-ssl.yml acme.yml
```

If you want to use ZeroSSL you need to sign-up there first, than create file `acme_configuration/zero-ssl.private` with content:
```
kid: 
key: 
alg: HS256
```
and put there `key id` and `key` from developer section on ZeroSSL.

## Example with CZERTAINLY
```
ansible-playbook -e @acme_configuration/czertainly.yml acme.yml
```

For DNS method you have to provide DNS server capable of dynamic updates, put needed parameters into acme_configuration/czertainly.private file:
```
server: 123.123.123.123
key_algorithm: "hmac-sha512"
key_name: "key"
key_secret: "secret"
```

## Note
Code inspired by https://github.com/semik/ansible-acme-demo

To complicated? You can use [acme.sh](https://github.com/acmesh-official/acme.sh/tree/master) it is written in shell and has much broader support for [free SSL certificate priders](https://github.com/acmesh-official/acme.sh/tree/master#supported-ca).
