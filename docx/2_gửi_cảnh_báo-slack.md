# GỬI CẢNH BÁO QUA SLACK.


CÁC BƯỚC TIẾN HÀNH:


## BƯỚC 1: LẤY URL WEBHOOK SLACK

https://api.slack.com/messaging/webhooks


NHỚ ĐĂNG NHẬP SLACK TRÊN CHOME SẴN NHA.\


![hinh ](./images/5.png)


![hinh ](./images/6.png)


![hinh ](./images/8.png)

![hinh ](./images/9.png)

![hinh ](./images/10.png)

![hinh ](./images/11.png)


COPY CÁI URL NÀY NHA. ĐỪNG ĐỂ THẤT LẠC.

![hinh ](./images/12.png)


## BƯỚC 2: CHỈNH SỬA FILE CẤU HÌNH CỦA ALERTMANAGER.

ta sẽ chỉnh sửa file config.yaml của alertmanager.




```
route:
    receiver: 'slack'

receivers:
    - name: 'slack'
      slack_configs:
          - send_resolved: true
            text: "{{ .CommonAnnotations.description }}"
            username: 'Prometheus'
            channel: '#app-monitoring'
            api_url: 'https://hooks.slack.com/services/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'
    
```



## KẾT QUẢ.
![hinh ](./images/13.png)

---

*DANH MỤC THAM KHẢO*

[1] https://www.youtube.com/watch?v=2E6GH9rAUwU&t=605s