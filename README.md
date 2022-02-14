# squid-proxyCache

referencia https://github.com/sameersbn/docker-squid 

el conf/squid.conf fue modificado quedando listo para usar

docker build -t squid .

docker run --name squid -d --restart=always \
  --publish 3128:3128 \
  --volume $(pwd)/conf/squid.conf:/etc/squid/squid.conf \
  --volume $(pwd)/squid/cache:/var/spool/squid \
  squid


luego se puede utilizar en docker para acelerar descargas repetitivas:
docker build -t tu_imagen --build-arg HTTP_PROXY=http://172.17.0.1:3128 .

o bien desde otra pc configurar este proxy para cachear el trafico

http://IP_PC_CORRIENDO_EL_CONTAINER:3128