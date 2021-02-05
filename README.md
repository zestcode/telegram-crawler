

# 1.更新说明
之前的branch许多老旧的api不再使用，使用最新的telethon接口，
修改了请求信息和用户id的get_message的参数
https://docs.telethon.dev/en/latest/quick-references/client-reference.html
官方文档可以参考
数据库的结构不变


## 1.1. MySQL 配置

Execute `telegram.sql`
数据表格式
MySQL [telegram]> desc message;
+-----------------+--------------+------+-----+---------+----------------+
| Field           | Type         | Null | Key | Default | Extra          |
+-----------------+--------------+------+-----+---------+----------------+
| id              | bigint       | NO   | PRI | NULL    | auto_increment |
| message_id      | bigint       | YES  |     | NULL    |                |
| chat_id         | bigint       | NO   |     | NULL    |                |
| message         | text         | YES  |     | NULL    |                |
| date            | datetime     | YES  |     | NULL    |                |
| from_id         | bigint       | YES  |     | NULL    |                |
| is_reply        | tinyint(1)   | YES  |     | NULL    |                |
| reply_to_msg_id | bigint       | YES  |     | NULL    |                |
| is_channel      | tinyint(1)   | YES  |     | NULL    |                |
| is_group        | tinyint(1)   | YES  |     | NULL    |                |
| media_file      | varchar(255) | YES  |     | NULL    |                |
+-----------------+--------------+------+-----+---------+----------------+

## 1.2. Create your Telegram apps

URL：https://my.telegram.org/

Edit `client.py`
#添加你的账号id和hash
```python
# Telegram config
api_id = 123456  # Your api_id
api_hash = '1234562a3e03835d881624e28c6f1d50'  # Your api_hash
session_name = 'session_name'
proxy_param = (socks.SOCKS5, 'localhost', 1080)   # Proxy settings, if you need
```
# 2. Run
主要入口是start_crawl_message
```bash
# Crawl message
python start_crawl_message.py 
# Crawl user
python start_crawl_user.py
# Crawl contact user
python start_crawl_contact_user.py
```
