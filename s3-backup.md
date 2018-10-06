# backup a directory to s3 automatically.
ref: [aws tut](https://aws.amazon.com/getting-started/tutorials/backup-to-s3-cli/)

- Create a iam user with program access.

- `aws configure`
- create a bucket

ruby script
```ruby
d = Time.now.strftime("%Y-%m-%d")
r = `zip -r #{d}.zip /var/gogs/`
r = `aws s3 cp #{d}.zip s3://askthebuffalobackup/`
r = `rm #{d}.zip`
```

add the script to cron
```text
1 1 * * * /usr/bin/ruby /home/ec2-user/bin/scripts/codebackup.rb
```
