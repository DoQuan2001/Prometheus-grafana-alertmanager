# RULE CẢNH BÁO ALERT MANAGER.

### LƯU Ý: ĐẶT 30% ĐỂ TEST DỄ LẤY CẢNH BÁO CHO NHANH:)))

```

groups:
  - name: recording_rules
    rules:
      - record: CPU_use_metric
        expr: (1 - avg by(instance) (irate(node_cpu_seconds_total{mode="idle"}[1m]))) * 100

      - record: RAM_use_metric
        expr: (1 - (node_memory_MemFree_bytes / node_memory_MemTotal_bytes)) * 100

      - record: DISK_use_metric
        expr: 100 * (1 - (node_filesystem_free_bytes / node_filesystem_size_bytes))
  - name: host
    rules:
      - alert: HIGH CPU 
        expr: CPU_use_metric > 10
        for: 60s
        labels:
          CPU: "{{ printf \"%.2f\" $value }} %"
          annotations: ""

      - alert: HIGH RAM
        expr: RAM_use_metric > 10
        for: 60s
        labels:
          job: ""
          RAM: "{{ printf \"%.2f\" $value}} %"
          Annotations: ""


      - alert: HIGH DISK
        expr: DISK_use_metric > 10
        for: 60s
        labels:
          job: ""
          DISK: "{{ printf \"%.2f\" $value}} %"
          Annotations: ""

    
      


```