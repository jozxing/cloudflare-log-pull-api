# cloudflare-log-pull-api for centos7.不要更改目录，一定要放在/opt/cloudflare 下，当然也可自己修改配置信息，改目录。
需要先安装EFK(elasticsearch/filebeat/kibana)<br/>

##调用cloudflare LogPull API导入ELK 数据可视化，使用哨兵插件，实现接口预警。<br/>
使用：<br/>
git clone https://github.com/jozxing/cloudflare-log-pull-api.git<br/>
mv cloudflare-log-pull-api /opt/cloudflare<br/>

cd /opt/cloudflare<br/>
chmod +x run.sh feron<br/>
cp feron /usr/local/bin<br/>
crontab -e<br/>
&emsp;*/1 * * * * /bin/bash -c "/opt/cloudflare/run.sh --from-cron"<br/>
##修改run.sh 里的配置信息<br/>
CF_ZONE_ID='xxxxxxxxx'<br/>
CF_AUTH_EMAIL='xxxxxxxxxxxxx'<br/>
CF_AUTH_KEY='cccccccccccc'<br/>

##全量还是按比例抽取日志样本配置，0.01表示1%流量，默认是1%，手动填写比例，需要全量填写1即可。<br/>
SAMPLE_RATE='0.01'    <br/>

其中export PATH，需要手动echo $PATH 环境变量，然后修改环境变量即可。<br/>

feron ----> https://github.com/anapsix/feron

致谢 LKK 运维大佬一起调试完成。

