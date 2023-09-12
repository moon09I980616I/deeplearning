# knockknkock_딥러닝 학습 프로세스 종료 시 알림 받기

[https://pypi.org/project/knockknock/#text-message-(sms)](https://pypi.org/project/knockknock/#text-message-(sms))

[https://coffee4m.com/디스코드-메신저-웹훅url/](https://coffee4m.com/%EB%94%94%EC%8A%A4%EC%BD%94%EB%93%9C-%EB%A9%94%EC%8B%A0%EC%A0%80-%EC%9B%B9%ED%9B%85url/)

### installation

`pip install knockknock`

### The knockknock Library -Usage Discord
```jsx
from knockknock import discord_sender

webhook_url = "<webhook_url_to_your_discord_channel>"
@discord_sender(webhook_url=webhook_url)
def train_your_nicest_model(your_nicest_parameters):
    import time
    time.sleep(10000)
    return {'loss': 0.9} # Optional return value
```
