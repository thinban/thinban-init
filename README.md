```
thinban-init
	base
		安装docker、docker-compose
		启动apt缓存服务
		启动nginx用来分发初始脚本
			public/
				thinban-init/
				01.init.sh
		主机配置apt代理
		主机安装其他常用软件
		go-dns
		#二期
		docker集群
		treafik
		自签名认证
		
	storage
		获取初始脚本并运行
			配置apt代理
			配置更新源
			更新软件
			配置dns
		mysql
		redis
		minio
		clickhouse
		etcd

	node
		k8s
			ref:storage
		flink
    
```