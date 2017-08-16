
```
shell> sudo apt-get update
shell> sudo apt-get install speedtest-cli
shell> brew install speedtest_cli
shell> speedtest-cli

Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from CHTD, Chunghwa Telecom Co., Ltd. (61.231.21.132)...
Selecting best server based on latency...
Hosted by Taiwan Fixed Network (New Taipei) [6.27 km]: 30.124 ms
Testing download speed........................................
Download: 86.75 Mbits/s
Testing upload speed..................................................
Upload: 16.22 Mbits/s

shell> speedtest-cli --share
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from CHTD, Chunghwa Telecom Co., Ltd. (61.231.21.132)...
Selecting best server based on latency...
Hosted by Chief Telecom (New Taipei) [6.27 km]: 27.405 ms
Testing download speed........................................
Download: 86.50 Mbits/s
Testing upload speed..................................................
Upload: 31.81 Mbits/s
Share results: http://www.speedtest.net/result/3915275618.png

shell> speedtest-cli --list
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
4505) Chief Telecom (New Taipei, Taiwan) [6.27 km]
5219) Taiwan Fixed Network (New Taipei, Taiwan) [6.27 km]
5067) Far Eastone Telecommunications Co., Ltd. (New Taipei, Taiwan) [6.27 km]
5334) Taiwan Star Telecom Co., Ltd. (New Taipei, Taiwan) [6.27 km]
5315) Taiwan Star Telecom Co., Ltd. (Taipei, Taiwan) [7.94 km]
5056) Taipei Fiber (Taipei, Taiwan) [7.94 km]
2133) Taiwan Fixed Network (Taipei, Taiwan) [7.94 km]
2327) Far Eastone Telecommunications Co., Ltd. (Taipei, Taiwan) [7.94 km]
2188) TFN Media Co., Ltd. (Taipei, Taiwan) [7.94 km]
3967) Chief Telecom (Taipei, Taiwan) [7.94 km]
5008) Asia Pacific Telecom (Taipei, Taiwan) [7.94 km]
2181) kbro Co., Ltd. (Taipei, Taiwan) [7.94 km]
5335) Taiwan Star Telecom Co., Ltd. (Taoyuan, Taiwan) [17.49 km]
2589) Far EasTone Telecommunications Co., Ltd (Taoyuan, Taiwan) [24.09 km]
4938) Chief Telecom (Taoyuan, Taiwan) [24.09 km]
3921) Taiwan Fixed Network (Taoyuan, Taiwan) [24.09 km]
5194) Taiwan Fixed Network (Yilan, Taiwan) [51.94 km]
4947) Chief Telecom (Yilan, Taiwan) [51.94 km]
......
4979) DeltaTelecom (Cafelandia, Brazil) [19502.85 km]
4430) CLICKNETRS (Sao Paulo das Missoes, Brazil) [19528.99 km]
4461) OpcaoNet Telecom (Nova Santa Rosa, Brazil) [19547.63 km]
5126) Cabletel Mercedes (Mercedes, Argentina) [19553.14 km]
5494) PIPELINE (Ciudad del Este, Paraguay) [19617.76 km]
3773) Sol Internet (Santa Rita, Paraguay) [19640.96 km]
4885) Sur Multimedia SA (Encarnacion, Paraguay) [19650.65 km]
1480) Telecel SA (Asuncion, Paraguay) [19924.66 km]
2830) Núcleo S.A., Personal (Asuncion, Paraguay) [19924.66 km]
2619) COPACO S.A. (Asuncion, Paraguay) [19924.66 km]

shell> speedtest-cli --server 4751
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from CHTD, Chunghwa Telecom Co., Ltd. (61.231.21.132)...
Hosted by Beijing Telecom (Beijing) [1717.40 km]: 99.503 ms
Testing download speed........................................
Download: 42.74 Mbits/s
Testing upload speed..................................................
Upload: 7.13 Mbits/s
```
