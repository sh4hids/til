## Running and accessing dynamodb locally with docker

- Need to set `user` to `root` to avoid Sequelize error
- Access DB using aws CLI: `aws dynamodb --endpoint-url=http://localhost:8000 list-tables`
- Generate Update Params:
```js
export function generateUpdateParams(inputs = {}) {
  if (!Object.keys(inputs).length) {
    return {};
  }

  return {
    ExpressionAttributeNames: Object.keys(inputs).reduce(
      (reduced, item) => Object.assign(reduced, { [`#n_${item}`]: item }),
      {}
    ),
    ExpressionAttributeValues: Object.keys(inputs).reduce(
      (reduced, item) =>
        Object.assign(reduced, { [`:v_${item}`]: inputs[item] }),
      {}
    ),
    UpdateExpression: `SET ${String(
      Object.keys(inputs).reduce(
        (reduced, item) => `${reduced}#n_${item} = :v_${item},`,
        ""
      )
    ).slice(0, -1)}`,
  };
}
```
