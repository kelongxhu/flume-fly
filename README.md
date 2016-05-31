数据源  ["a","b","d"]


flume配置

a1.sources=source1
a1.sinks=sink1
a1.channels=channel1


a1.sources.source1.type = exec
a1.sources.source1.command = tail -n 0 -F /data/log/access.log
a1.sources.source1.channels = channel1
#a1.sources.source1.interceptors = i1
#a1.sources.source1.interceptors.i1.type = timestamp
a1.sinks.sink1.type =org.apache.flume.sink.elasticsearch.ElasticSearchSink
a1.sinks.sink1.batchSize =100
a1.sinks.sink1.hostNames =127.0.0.1:9300
a1.sinks.sink1.indexName =test2
a1.sinks.sink1.indexType =fish2
a1.sinks.sink1.clusterName =cluster
a1.sinks.sink1.serializer=com.fish.flume.sink.elasticsearch.ElasticSearchNginxEventSerializer
a1.sinks.sink1.serializer.fields=filed1 filed2 filed3
#a1.sinks.sink1.serializer.fields.filed1.serializer=int
#a1.sinks.sink1.serializer.fields.time_local.serializer=date
#a1.sinks.sink1.serializer.fields.time_local.format=dd/MMMMM/yyyy:HH:mm:ss z
#a1.sinks.sink1.serializer.fields.time_local.locale=en

a1.channels.channel1.type =memory
a1.channels.channel1.capacity =1000000
a1.channels.channel1.transactionCapacity =5000

a1.sinks.sink1.channel =channel1


# flume-fly
