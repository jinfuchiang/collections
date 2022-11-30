## [如何在 UEFI 启用 Secure Boot 模式下安装第三方（自己写的）驱动](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/managing_monitoring_and_updating_the_kernel/index#signing-kernel-modules-for-secure-boot_managing-monitoring-and-updating-the-kernel)
1. 创建 X.509 公私钥对
```shell
# cat << EOF > configuration_file.config
[ req ]
default_bits = 4096
distinguished_name = req_distinguished_name
prompt = no
string_mask = utf8only
x509_extensions = myexts

[ req_distinguished_name ]
O = Organization
CN = Organization signing key
emailAddress = E-mail address

[ myexts ]
basicConstraints=critical,CA:FALSE
keyUsage=digitalSignature
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid
EOF
# openssl req -x509 -new -nodes -utf8 -sha256 -days 36500 \
-batch -config configuration_file.config -outform DER \
-out my_signing_key_pub.der \
-keyout my_signing_key.priv
```
2. 注册公钥至 MOK 列表
```shell
# mokutil --import my_signing_key_pub.der
```
- 注册完后重启，在 UEFI 界面确认添加
3. 用```sign-file```对 ko 文件签名
sign-file 属于内核提供的 utility，可使用 `dpkg -S sign-file` 搜素它的路径
```shell
# /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 my_signing_key.priv my_signing_key_pub.der my_module.ko
```
4. 安装该驱动
```insmod my_module.ko```
5. 三种验证安装成功方法方法
  - 使用 lsmod：```lsmod | grep my_module.ko```
  - 使用 dmesg（printk 的内容会显示至此）：```dmesg```
  - 查看 /var/log/syslog
