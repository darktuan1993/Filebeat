docker run \
  --user=root \
  --name=filebeat_isofh \
  -v /var/run/docker.sock:/host_docker/docker.sock \
  -v /var/lib/docker:/host_docker/var/lib/docker \
  -v /home/isofh/server/emr/tttm-production/his/log:/usr/share/filebeat/mylog \
  -v /root/filebeat/filebeat.yml:/usr/share/filebeat/filebeat.yml \
  -e "strict.perms=false" \
  --memory=200MB \
  --ulimit memlock=-1:-1 \
  -i \
  -t \
  --network=bridge \
  docker.elastic.co/beats/filebeat:7.5.0
