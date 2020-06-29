```
git submodule add https://github.com/rin-ofumi/m5stickc_co2_hat.git
git submodule add https://github.com/micropython/micropython.git

mkdir co2hat
mkdir co2hat/apps

cp -p m5stickc_co2_hat/CO2_zeropoint.py ./co2hat/apps/zeropoint.py
cp -p m5stickc_co2_hat/test_CO2_Ambient.py ./co2hat/apps/CO2_Ambiet.py
cp -p m5stickc_co2_hat/co2_set.txt ./co2hat/

cp -p micropython/ports/esp8266/modules/ntptime.py ./co2hat/
sed -i -e "s/NTP_DELTA = 3155673600/NTP_DELTA = 3155673600 - (9*60*60)/" ./co2hat/ntptime.py
diff co2hat/ntptime.py micropython/ports/esp8266/modules/ntptime.py
```
