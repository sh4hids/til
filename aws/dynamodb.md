## Running and accessing dynamodb locally with docker

- Need to set `user` to `root` to avoid Sequelize error
- Access DB using aws CLI: `aws dynamodb --endpoint-url=http://localhost:8000 list-tables`
