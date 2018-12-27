# ClamAV setup on RHEL/CentOS 7

How to setup ClamAV on RHEL/CentOS 7.

## 1.Installation

You need to install the following packages

```bash
yum -y install epel-release;yum -y update;
yum -y install clamav clamav-data clamav-scanner clamav-scanner-systemd clamav-server clamav-server-systemd clamav-unofficial-sigs clamav-update

```

## 2.Copy the following config files
1-freshclam.conf  --> /etc/clamd.d/freshclam.conf
2-clamav-freshclam.service --> /usr/lib/systemd/system/clamav-freshclam.service

## 3.Run the following commands
```bash
systemctl enable clamav-freshclam.service;
systemctl start clamav-freshclam.service;
setsebool -P antivirus_can_scan_system 1;
setsebool -P antivirus_use_jit 1;
```

## 4.Copy the following config files
3-scan.conf  --> /etc/clamd.d/scan.conf
4-clamd@.service --> /usr/lib/systemd/system/clamd@.service


## 5.Run the following commands
```bash
systemctl enable clamd@scan.service; systemctl start clamd@scan.service;
```


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
