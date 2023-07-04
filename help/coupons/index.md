# Coupon Module Usage:

Variables:

| Variable           | Description                      |
| ------------------ | -------------------------------- |
| @{{coupon.code}}   | Coupon code on successfull allot |
| @{{coupon.status}} | Response status                  |

### Status Codes

These status codes can be obtained from `@{{coupon.status}}`

#### On Allot:

| Status Code          | Description                               |
| -------------------- | ----------------------------------------- |
| COUPON_ALLOC_SUCCESS | Coupon successfully allocated to a number |
| COUPON_LIMIT_REACHED | Coupon alloc limit reached for a number   |

#### On Redeem:

| Status Code    | Description        |
| -------------- | ------------------ |
| COUPON_INVALID | Invalid coupon     |
| REDEEM_SUCCESS | Redeem successfull |
