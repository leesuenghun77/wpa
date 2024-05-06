# wpa
wpa 보안
#!/bin/bash

# 무선 네트워크 인터페이스 설정
INTERFACE="wlan0"

# SSID 및 비밀번호 설정
SSID="your_ssid"
PASSWORD="your_password"

# WPA supplicant 설정 파일 경로
WPA_CONF="/etc/wpa_supplicant/wpa_supplicant.conf"

# WPA 연결 설정
wpa_passphrase "$SSID" "$PASSWORD" > "$WPA_CONF"
wpa_supplicant -B -i "$INTERFACE" -c "$WPA_CONF"

# IP 주소 할당
dhclient "$INTERFACE"

echo "WPA 연결이 완료되었습니다."
