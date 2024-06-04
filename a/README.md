# screwdriver-dev-test

| TH                                    | TH        | TH          |
|---------------------------------------|-----------|-------------|
| 1-1-~a-succeed-triggered              | a✅        | トリガーされる     |
| 1-1-~a-failure-not-triggered          | a❌        | トリガーされない    |
| 1-1-~a-restart-triggered              | a❌ -> a🔄 | トリガーされる     |
| 1-1-~a-multiple-succeed-triggered     | a✅        | 1度だけトリガーされる |
| 1-1-~a-multiple-failure-not-triggered | a❌        | トリガーされない    |
| 1-1-~a-multiple-restart-triggered     | a❌ -> a🔄 | 1度だけトリガーされる |
| -                                     |           | -           |
| 2-1-a-succeed-triggered               | a✅        | トリガーされる     |
| 2-1-a-failure-not-triggered           | a❌        | トリガーされない    |
| 2-1-a-restart-triggered               | a❌ -> a🔄 | トリガーされる     |
| 2-1-a-multiple-succeed-triggered      | a✅        | 1度だけトリガーされる |
| 2-1-a-multiple-failure-not-triggered  | a❌        | トリガーされない    |
| 2-1-a-multiple-restart-triggered      | a❌ -> a🔄 | 1度だけトリガーされる |

| TH                                                         | TH                              | TH              |
|------------------------------------------------------------|---------------------------------|-----------------|
| [~a,~b]-succeed-a-b-triggered                              | a✅、b✅                           | トリガーされる         |
| [~a,~b]-succeed-a-triggered                                | a✅、b❌                           | トリガーされる         |
| [~a,~b]-failure-a-b-not-triggered                          | a❌、b❌                           | トリガーされない        |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a❌              | 1,2回目にトリガーされる   |
| [~a,~b]-restart4                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a,~b]-restart3                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [~a,~b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a,~b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b✅ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b✅ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [~a,~b]-succeed-a-restart-a-succeed-a-triggered            | a✅、b❌ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-restart-a-failed-a-not-triggered         | a✅、b❌ -> a🔄 -> a❌              | 1回目にトリガーされる     |
| [~a,~b]-succeed-a-restart-b-succeed-b-succeed              | a✅、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [~a,~b]-succeed-a-restart-b-failed-b-triggered             | a✅、b❌ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [~a,~b]-restart4                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a,~b]-restart3                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [~a,~b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,3回目にトリガーされる   |
| [~a,~b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1回目にトリガーされる     |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b❌ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [~a,~b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b❌ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [~a,~b]-succeed-a-restart-a-succeed-a-triggered            | a❌、b❌ -> a🔄 -> a✅              | 2回目にトリガーされる     |
| [~a,~b]-succeed-a-restart-a-failed-a-not-triggered         | a❌、b❌ -> a🔄 -> a❌              | トリガーされない        |
| [~a,~b]-succeed-a-restart-b-succeed-b-succeed              | a❌、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [~a,~b]-succeed-a-restart-b-failed-b-triggered             | a❌、b❌ -> b🔄 -> b❌              | トリガーされない        |
| [~a,~b]-restart4                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 2,3回目にトリガーされる   |
| [~a,~b]-restart3                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 2回目にトリガーされる     |
| [~a,~b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 3回目にトリガーされる     |
| [~a,~b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | トリガーされない        |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a❌、b❌ -> a,b🔄 -> a✅、b✅         | 2回目にトリガーされる     |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a✅、b❌         | 2回目にトリガーされる     |
| [~a,~b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a❌、b✅         | 2回目にトリガーされる     |
| [~a,~b]-succeed-a-b-restart-a-failed-a-b-triggered         | a❌、b❌ -> a,b🔄 -> a❌、b❌         | トリガーされない        |

| TH                                                        | TH                              | TH              |
|-----------------------------------------------------------|---------------------------------|-----------------|
| [~a,b]-succeed-a-b-triggered                              | a✅、b✅                           | トリガーされる         |
| [~a,b]-succeed-a-triggered                                | a❌、b✅                           | トリガーされる         |
| [~a,b]-succeed-a-triggered                                | a✅、b❌                           | トリガーされる         |
| [~a,b]-failure-a-b-not-triggered                          | a❌、b❌                           | トリガーされない        |
| [~a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a❌              | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> b🔄 -> b✅              | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [~a,b]-restart4                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a,b]-restart3                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [~a,b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a,b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b✅ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b✅ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [~a,b]-succeed-a-restart-a-succeed-a-triggered            | a✅、b❌ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-restart-a-failed-a-not-triggered         | a✅、b❌ -> a🔄 -> a❌              | 1回目にトリガーされる     |
| [~a,b]-succeed-a-restart-b-succeed-b-succeed              | a✅、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [~a,b]-succeed-a-restart-b-failed-b-triggered             | a✅、b❌ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [~a,b]-restart4                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a,b]-restart3                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [~a,b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,3回目にトリガーされる   |
| [~a,b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1回目にトリガーされる     |
| [~a,b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b❌ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [~a,b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b❌ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [~a,b]-succeed-a-restart-a-succeed-a-triggered            | a❌、b❌ -> a🔄 -> a✅              | 2回目にトリガーされる     |
| [~a,b]-succeed-a-restart-a-failed-a-not-triggered         | a❌、b❌ -> a🔄 -> a❌              | トリガーされない        |
| [~a,b]-succeed-a-restart-b-succeed-b-succeed              | a❌、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [~a,b]-succeed-a-restart-b-failed-b-triggered             | a❌、b❌ -> b🔄 -> b❌              | トリガーされない        |
| [~a,b]-restart4                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 2,3回目にトリガーされる   |
| [~a,b]-restart3                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 2回目にトリガーされる     |
| [~a,b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 3回目にトリガーされる     |
| [~a,b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | トリガーされない        |
| [~a,b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a❌、b❌ -> a,b🔄 -> a✅、b✅         | 2回目にトリガーされる     |
| [~a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a✅、b❌         | 2回目にトリガーされる     |
| [~a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a❌、b✅         | 2回目にトリガーされる     |
| [~a,b]-succeed-a-b-restart-a-failed-a-b-triggered         | a❌、b❌ -> a,b🔄 -> a❌、b❌         | トリガーされない        |

| TH                                                       | TH                              | TH              |
|----------------------------------------------------------|---------------------------------|-----------------|
| [a,b]-succeed-a-b-triggered                              | a✅、b✅                           | トリガーされる         |
| [a,b]-succeed-a-triggered                                | a❌、b✅                           | トリガーされる         |
| [a,b]-succeed-a-triggered                                | a✅、b❌                           | トリガーされる         |
| [a,b]-failure-a-b-not-triggered                          | a❌、b❌                           | トリガーされない        |
| [a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a❌              | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> b🔄 -> b✅              | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [a,b]-restart4                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [a,b]-restart3                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [a,b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [a,b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b✅ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b✅ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [a,b]-succeed-a-restart-a-succeed-a-triggered            | a✅、b❌ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-restart-a-failed-a-not-triggered         | a✅、b❌ -> a🔄 -> a❌              | 1回目にトリガーされる     |
| [a,b]-succeed-a-restart-b-succeed-b-succeed              | a✅、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [a,b]-succeed-a-restart-b-failed-b-triggered             | a✅、b❌ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [a,b]-restart4                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [a,b]-restart3                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [a,b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,3回目にトリガーされる   |
| [a,b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1回目にトリガーされる     |
| [a,b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b❌ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [a,b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b❌ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [a,b]-succeed-a-restart-a-succeed-a-triggered            | a❌、b❌ -> a🔄 -> a✅              | 2回目にトリガーされる     |
| [a,b]-succeed-a-restart-a-failed-a-not-triggered         | a❌、b❌ -> a🔄 -> a❌              | トリガーされない        |
| [a,b]-succeed-a-restart-b-succeed-b-succeed              | a❌、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [a,b]-succeed-a-restart-b-failed-b-triggered             | a❌、b❌ -> b🔄 -> b❌              | トリガーされない        |
| [a,b]-restart4                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 2,3回目にトリガーされる   |
| [a,b]-restart3                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 2回目にトリガーされる     |
| [a,b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 3回目にトリガーされる     |
| [a,b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | トリガーされない        |
| [a,b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a❌、b❌ -> a,b🔄 -> a✅、b✅         | 2回目にトリガーされる     |
| [a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a✅、b❌         | 2回目にトリガーされる     |
| [a,b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a❌、b✅         | 2回目にトリガーされる     |
| [a,b]-succeed-a-b-restart-a-failed-a-b-triggered         | a❌、b❌ -> a,b🔄 -> a❌、b❌         | トリガーされない        |

# [ ~a, a, b ]

| TH                                                            | TH                              | TH              |
|---------------------------------------------------------------|---------------------------------|-----------------|
| [~a, a, b]-succeed-a-b-triggered                              | a✅、b✅                           | トリガーされる         |
| [~a, a, b]-succeed-a-triggered                                | a❌、b✅                           | トリガーされる         |
| [~a, a, b]-succeed-a-triggered                                | a✅、b❌                           | トリガーされる         |
| [~a, a, b]-failure-a-b-not-triggered                          | a❌、b❌                           | トリガーされない        |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> a🔄 -> a❌              | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> b🔄 -> b✅              | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-triggered          | a✅、b✅ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [~a, a, b]-restart4                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a, a, b]-restart3                                           | a✅、b✅ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [~a, a, b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a, a, b]-restart3                                           | a✅、b✅ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b✅ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b✅ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b✅ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [~a, a, b]-succeed-a-restart-a-succeed-a-triggered            | a✅、b❌ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-restart-a-failed-a-not-triggered         | a✅、b❌ -> a🔄 -> a❌              | 1回目にトリガーされる     |
| [~a, a, b]-succeed-a-restart-b-succeed-b-succeed              | a✅、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [~a, a, b]-succeed-a-restart-b-failed-b-triggered             | a✅、b❌ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |
| [~a, a, b]-restart4                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |
| [~a, a, b]-restart3                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |
| [~a, a, b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,3回目にトリガーされる   |
| [~a, a, b]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1回目にトリガーされる     |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b❌ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |
| [~a, a, b]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b❌ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |
| [~a, a, b]-succeed-a-restart-a-succeed-a-triggered            | a❌、b❌ -> a🔄 -> a✅              | 2回目にトリガーされる     |
| [~a, a, b]-succeed-a-restart-a-failed-a-not-triggered         | a❌、b❌ -> a🔄 -> a❌              | トリガーされない        |
| [~a, a, b]-succeed-a-restart-b-succeed-b-succeed              | a❌、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |
| [~a, a, b]-succeed-a-restart-b-failed-b-triggered             | a❌、b❌ -> b🔄 -> b❌              | トリガーされない        |
| [~a, a, b]-restart4                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 2,3回目にトリガーされる   |
| [~a, a, b]-restart3                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 2回目にトリガーされる     |
| [~a, a, b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 3回目にトリガーされる     |
| [~a, a, b]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | トリガーされない        |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a❌、b❌ -> a,b🔄 -> a✅、b✅         | 2回目にトリガーされる     |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a✅、b❌         | 2回目にトリガーされる     |
| [~a, a, b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a❌、b✅         | 2回目にトリガーされる     |
| [~a, a, b]-succeed-a-b-restart-a-failed-a-b-triggered         | a❌、b❌ -> a,b🔄 -> a❌、b❌         | トリガーされない        |

# [ ~a, b, c ]

| TH                                 | TH       | TH       |
|------------------------------------|----------|----------|
| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ | トリガーされる  |
| [~a,b,c]-succeed-a-triggered       | a❌、b✅、c✅ | トリガーされる  |
| [~a,b,c]-succeed-a-triggered       | a✅、b❌、c✅ | トリガーされる  |
| [~a,b,c]-succeed-a-triggered       | a❌、b❌、c✅ | トリガーされない |
| [~a,b,c]-succeed-a-triggered       | a✅、b❌、c❌ | トリガーされる  |
| [~a,b,c]-failure-a-b-not-triggered | a❌、b❌、c❌ | トリガーされない |

# [ ~sd@1:a ]

1: 上流パイプライン

| TH                                | TH       |
|-----------------------------------|----------|
| ~sd@1:a✅                          | トリガーされる  |
| ~sd@1:a❌                          | トリガーされない |
| ~sd@1:a✅ -> ~sd@1:a🔄 -> ~sd@1:a✅ | トリガーされる  |
| ~sd@1:a✅ -> ~sd@1:a🔄 -> ~sd@1:a❌ | トリガーされない |
| ~sd@1:a❌ -> ~sd@1:a🔄 -> ~sd@1:a✅ | トリガーされる  |
| ~sd@1:a❌ -> ~sd@1:a🔄 -> ~sd@1:a❌ | トリガーされない |

2: 下流パイプライン

| TH                                | TH       |
|-----------------------------------|----------|
| ~sd@1:a✅                          | トリガーされる  |
| ~sd@1:a❌                          | トリガーされない |
| ~sd@1:a✅ -> ~sd@1:a🔄 -> ~sd@1:a✅ | トリガーされる  |
| ~sd@1:a✅ -> ~sd@1:a🔄 -> ~sd@1:a❌ | トリガーされない |
| ~sd@1:a❌ -> ~sd@1:a🔄 -> ~sd@1:a✅ | トリガーされる  |
| ~sd@1:a❌ -> ~sd@1:a🔄 -> ~sd@1:a❌ | トリガーされない |

# [ sd@1:a ]

1: 上流パイプライン

| TH                             | TH       |
|--------------------------------|----------|
| sd@1:a✅                        | トリガーされる  |
| sd@1:a❌                        | トリガーされない |
| sd@1:a✅ -> sd@1:a🔄 -> sd@1:a✅ | トリガーされる  |
| sd@1:a✅ -> sd@1:a🔄 -> sd@1:a❌ | トリガーされない |
| sd@1:a❌ -> sd@1:a🔄 -> sd@1:a✅ | トリガーされる  |
| sd@1:a❌ -> sd@1:a🔄 -> sd@1:a❌ | トリガーされない |

2: 下流パイプライン

| TH                             | TH       |
|--------------------------------|----------|
| sd@1:a✅                        | トリガーされない |
| sd@1:a❌                        | トリガーされない |
| sd@1:a✅ -> sd@1:a🔄 -> sd@1:a✅ | トリガーされない |
| sd@1:a✅ -> sd@1:a🔄 -> sd@1:a❌ | トリガーされない |
| sd@1:a❌ -> sd@1:a🔄 -> sd@1:a✅ | トリガーされない |
| sd@1:a❌ -> sd@1:a🔄 -> sd@1:a❌ | トリガーされない |

# [ ~sd@1:a, ~sd@1:a ]

| TH              | TH        | TH      |
|-----------------|-----------|---------|
| a✅              | 上流パイプライン, | トリガーされる |
| a✅              | トリガーされる   |
| a❌              | トリガーされない  |
| a❌              | トリガーされない  |
| a✅ -> a🔄 -> a✅ | トリガーされる   |
| a✅ -> a🔄 -> a❌ | トリガーされない  |
| a❌ -> a🔄 -> a✅ | トリガーされる   |
| a❌ -> a🔄 -> a❌ | トリガーされない  |

# [ sd@1:a ]

| TH              | TH        | TH      |
|-----------------|-----------|---------|
| a✅              | 上流パイプライン, | トリガーされる |
| a✅              | トリガーされる   |
| a❌              | トリガーされない  |
| a❌              | トリガーされない  |
| a✅ -> a🔄 -> a✅ | トリガーされる   |
| a✅ -> a🔄 -> a❌ | トリガーされない  |
| a❌ -> a🔄 -> a✅ | トリガーされる   |
| a❌ -> a🔄 -> a❌ | トリガーされない  |

# [ sd@1:a, sd@1:a ]

| TH              | TH        | TH      |
|-----------------|-----------|---------|
| a✅              | 上流パイプライン, | トリガーされる |
| a✅              | トリガーされる   |
| a❌              | トリガーされない  |
| a❌              | トリガーされない  |
| a✅ -> a🔄 -> a✅ | トリガーされる   |
| a✅ -> a🔄 -> a❌ | トリガーされない  |
| a❌ -> a🔄 -> a✅ | トリガーされる   |
| a❌ -> a🔄 -> a❌ | トリガーされない  |

[//]: # (| TH                             | TH       |)

[//]: # (|--------------------------------|----------|)

[//]: # (| sd@2:a✅                        | トリガーされる  |)

[//]: # (| sd@2:a❌                        | トリガーされない |)

[//]: # (| sd@2:a✅ -> sd@2:a🔄 -> sd@2:a✅ | トリガーされる  |)

[//]: # (| sd@2:a✅ -> sd@2:a🔄 -> sd@2:a❌ | トリガーされる  |)

[//]: # (| sd@2:a❌ -> sd@2:a🔄 -> sd@2:a✅ | トリガーされる  |)

[//]: # (| sd@2:a❌ -> sd@2:a🔄 -> sd@2:a❌ | トリガーされない |)

[//]: # (| sd@2:a✅ -> sd@1:a🔄 -> sd@2:a✅ | トリガーされる  |)

[//]: # (| sd@2:a✅ -> sd@1:a🔄 -> sd@2:a❌ | トリガーされる  |)

[//]: # (| sd@2:a❌ -> sd@1:a🔄 -> sd@2:a✅ | トリガーされる  |)

[//]: # (| sd@2:a❌ -> sd@1:a🔄 -> sd@2:a❌ | トリガーされない |)


[//]: # (       | [~a,b,c]-succeed-a-b-triggered | a✅、b✅、c✅ -> a🔄 -> a✅ | トリガーされる         |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> a🔄 -> a❌              | トリガーされる         |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> b🔄 -> b✅              | トリガーされる         |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> b🔄 -> b❌              | トリガーされる         |)

[//]: # (| [a,b]-restart4                     | a✅、b✅、c✅ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |)

[//]: # (| [a,b]-restart3                     | a✅、b✅、c✅ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |)

[//]: # (| [a,b]-restart3                     | a✅、b✅、c✅ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |)

[//]: # (| [a,b]-restart3                     | a✅、b✅、c✅ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> a,b,c🔄 -> a✅、b✅       | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> a,b,c🔄 -> a✅、b❌       | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> a,b,c🔄 -> a❌、b✅       | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-triggered     | a✅、b✅、c✅ -> a,b,c🔄 -> a❌、b❌       | 1回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-restart-a-succeed-a-triggered            | a✅、b❌ -> a🔄 -> a✅              | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-restart-a-failed-a-not-triggered         | a✅、b❌ -> a🔄 -> a❌              | 1回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-restart-b-succeed-b-succeed              | a✅、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-restart-b-failed-b-triggered             | a✅、b❌ -> b🔄 -> b❌              | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-restart4                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 1,2,3回目にトリガーされる |)

[//]: # (| [~a,b,c]-restart3                                           | a✅、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 1,2,3回目にトリガーされる |)

[//]: # (| [~a,b,c]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 1,3回目にトリガーされる   |)

[//]: # (| [~a,b,c]-restart3                                           | a✅、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | 1回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-succeed-a-b-triggered        | a✅、b❌ -> a,b🔄 -> a✅、b✅         | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a✅、b❌         | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a✅、b❌ -> a,b🔄 -> a❌、b✅         | 1,2回目にトリガーされる   |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-failed-a-b-triggered         | a✅、b❌ -> a,b🔄 -> a❌、b❌         | 1回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-restart-a-succeed-a-triggered            | a❌、b❌ -> a🔄 -> a✅              | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-restart-a-failed-a-not-triggered         | a❌、b❌ -> a🔄 -> a❌              | トリガーされない        |)

[//]: # (| [~a,b,c]-succeed-a-restart-b-succeed-b-succeed              | a❌、b❌ -> b🔄 -> b✅              | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-restart-b-failed-b-triggered             | a❌、b❌ -> b🔄 -> b❌              | トリガーされない        |)

[//]: # (| [~a,b,c]-restart4                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b✅ | 2,3回目にトリガーされる   |)

[//]: # (| [~a,b,c]-restart3                                           | a❌、b❌ -> a🔄 -> a✅ -> b🔄 -> b❌ | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b✅ | 3回目にトリガーされる     |)

[//]: # (| [~a,b,c]-restart3                                           | a❌、b❌ -> a🔄 -> a❌ -> b🔄 -> b❌ | トリガーされない        |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-succeed-a-b-triggered        | a❌、b❌ -> a,b🔄 -> a✅、b✅         | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a✅、b❌         | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a❌、b✅         | 2回目にトリガーされる     |)

[//]: # (| [~a,b,c]-succeed-a-b-restart-a-failed-a-b-triggered         | a❌、b❌ -> a,b🔄 -> a❌、b❌         | トリガーされない        |)

[//]: # ()

[//]: # ()

[//]: # ()

[//]: # (| [~a,~b]-succeed-a-b-restart-a-succeed-a-b-triggered        | a❌、b❌ -> a,b🔄 -> a✅、b✅      | [ ~a, ~b ] がトリガーされる     |)

[//]: # (| [~a,~b]-succeed-a-b-restart-a-succeed-a-failed-b-triggered | a❌、b❌ -> a,b🔄 -> a✅、b❌      | [ ~a, ~b ] がトリガーされる     |)

[//]: # (| [~a,~b]-succeed-a-b-restart-a-failed-a-b-triggered         | a❌、b❌ -> a,b🔄 -> a❌、b❌      | [ ~a, ~b ] がトリガーされない    |)

[//]: # (| 3-5-~a-~b-restart3                                         | a❌、b❌ -> a🔄 -> b🔄 -> a❌、b❌ | [ ~a, ~b ] がトリガーされない    |)

[//]: # (| 3-5-~a-~b-restart3                                         | a❌、b❌ -> a🔄 -> b🔄 -> a✅、b❌ | [ ~a, ~b ] が1度だけトリガーされる |)

[//]: # (| 3-5-~a-~b-restart4                                         | a❌、b❌ -> a🔄 -> b🔄 -> a✅、b✅ | [ ~a, ~b ] が1度だけトリガーされる |)

[//]: # (| 3-4-~a-~b-restart4                                         | a✅、b❌ -> a,b🔄               | [ ~a, ~b ] がトリガーされる     |)

[//]: # (| 3-5-~a-~b-restart6                                         | a❌、b❌ -> a,b🔄               | [ ~a, ~b ] がトリガーされる     |)
