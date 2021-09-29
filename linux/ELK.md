# ELK(日志系统)



参考：https://blog.csdn.net/qq_34988304/article/details/100058049



```
input {
  beats {
    port => 7044
  }
  tcp {
    port => 7569
    codec => json{
        charset => "UTF-8"
    }
  }
}


    <springProperty scope="context" name="server.name" source="spring.application.name" defaultValue="zy-default"/>
	<!-- logstash设置 -->
    <appender name="logstash" class="net.logstash.logback.appender.LogstashTcpSocketAppender">
        <param name="Encoding" value="UTF-8"/>
        <!-- logstash服务器ip -->
        <remoteHost>223.84.147.58</remoteHost>
        <!-- logstash tcp 端口-->
        <port>7569</port>
        <queueSize>1048576</queueSize>
        <!-- <filter class="com.program.interceptor.ELKFilter"/>-->
        <!-- encoder is required -->
        <encoder charset="UTF-8" class="net.logstash.logback.encoder.LogstashEncoder" >
            <customFields>{"appname":"${server.name}"}</customFields>
        </encoder>
    </appender>
```

