# README

I created seperate value files and this readme. Those are the only files which you should do changes in. Then we should be able to rebase always from upstream

#Local Dev
```
$  cd ./charts
$  helm upgrade home-assistant-rpu ./home-assistant  --values home-assistant/values-rpu.yaml --namespace=homeassistant
```

## Copy Backup from k8s

```bash
# kubectl cp default/POD_NAME:bin/FILE_NAME /Users/username/FILE_NAME
$   kubectl cp -c home-assistant  homeassistant/home-assistant-rpu-0:config/backups/  ./backup/core_2025_10/homeassistant/data          
```

## Copy Backup to k8s

```bash
$  kubectl cp ./backup/container/homeassistant/data/ homeassistant/home-assistant-rpu-0:/config-bu -c home-assistant
```

## Notes

#Changed Local HA URL from http://10.42.0.33:8123 to local address


- Manually installed  HACS
```
wget -O - https://get.hacs.xyz | bash -
````

Rebase FORK with upstream

```
git fetch upstream
git checkout main
git rebase upstream/main

````