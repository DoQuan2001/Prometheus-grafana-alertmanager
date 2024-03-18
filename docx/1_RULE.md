# RULE CẢNH BÁO ALERT MANAGER.

### LƯU Ý: ĐẶT 30% ĐỂ TEST DỄ LẤY CẢNH BÁO CHO NHANH:)))


## I. VIẾT RULE TRONG FILE ALERT.RULES
```


groups:

- name: host
  rules:
  - alert: HIGH CPU 
    expr: (1 - avg by(instance) (irate(node_cpu_seconds_total{mode="idle"}[1m]))) * 100 > 10
    for: 60s
    labels:
      CPU: "{{ printf \"%.2f\" $value }} %"
 
  - alert: HIGH RAM
    expr: (1 - (node_memory_MemFree_bytes / node_memory_MemTotal_bytes)) * 100 >10
    for: 60s
    labels:
      job: ""
      RAM: "{{ printf \"%.2f\" $value}} %"
  

  - alert: HIGH DISK
    expr: 100 * (1 - (node_filesystem_free_bytes / node_filesystem_size_bytes)) > 10
    labels:
      job: ""
      device: ""
      fstype: ""
      DISK: "{{ printf \"%.2f\" $value}} %"
  
      








```



## II. VIẾT RULE TRONG GIAO DIỆN CỦA GRAFANA.


### 







## III. VIẾT RULE TRÊN GIAO DIỆN ALERT MANAGER.

 labels:
      job: ""
      device: ""
      fstype: ""
      instance: ""
      DISK: "{{ printf \"%.2f\" $value}} %"