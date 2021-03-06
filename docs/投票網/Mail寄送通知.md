# Mail 寄送通知

### 作業目的

> Mail 寄送通知

## 規格

| 項目                    | 說明                                         |
| ----------------------- | -------------------------------------------- |
| Method                  | POST                                         |
| Required Request Header | Content-Type:application/json; charset=UTF-8 |
| 測試 環境 API 地址      | /vote/schedule/mail                          |
| 通用格式                | 否                                           |
| authorization           | Bearer { token }                             |

## 請求

### Request 欄位

| 欄位名稱  | 資料型別 | 長度 | 必須       | 說明                                    |
| --------- | -------- | ---- | ---------- | --------------------------------------- |
| workNo    | string   | 6    | Y          | 作業代號                                |
| title     | string   | 不限 | 選填       | 投票主旨                                |
| starttime | string   | 20   | 選填       | 投票起始日 fmt yyyy-mm-dd hh:nn:ss      |
| endtime   | string   | 20   | 選填       | 投票截止日 fmt yyyy-mm-dd hh:nn:ss      |
| winner    | string   | 不限 | 選填       | 獲勝選項                                |
| setup1    | string   | 不限 | 選填       | 是否匿名 ..直接顯示白話文               |
| setup2    | string   | 不限 | 選填       | 一人幾票 ..直接顯示白話文               |
| actNo     | string   | 64   | 選填       | 依作業需求傳入 單號                     |
| subjet    | string   | 40   | 條件性必填 | 主旨 作業代號 VOTS04、VOTS05 時必填     |
| content   | string   | 4084 | 條件性必填 | 意見回饋 作業代號 VOTS04、VOTS05 時必填 |

### 作業代號簡述

| 作業代號 | 作業功能             |
| -------- | -------------------- |
| VOTS01   | 活動通知 Mail        |
| VOTS02   | 催票通知 Mail        |
| VOTS03   | 活動結束 Mail        |
| VOTS04   | 聯繫我們             |
| VOTS05   | 審核失敗的 mail 寄送 |
| VOTS06   | 訂單拋轉結案寄送通知 |
| VOTS07   | 關通知             |

### Request 範例

```json
{
  "workNo": "VOTS01",
  "title": "天不生我許寧夜，此道萬古如長夜",
  "starttime ": "2020-08-01 09:18:21",
  "endtime": "2020-08-02 09:18:33",
  "winner": "許寧夜",
  "setup1": "匿名投票",
  "setup2": "一人4票",
  "actNo": "20200803140000A00001"
}
```

## 回應

> 簡單的回應訊息，來確定是否存檔成功
> 使用通用格式 code 0 msg succese

### Response 範例

```json
{
  "state": 200,
  "msg": "succese",
  "error": "",
  "data": {}
}
```
