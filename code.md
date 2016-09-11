
### Code Structure
* 所有的 service 都是透過 return false 和 .errors.full_messages 來處理錯誤， controller 都會用這樣的邏輯來處理
* 用service 來架構整個系統, controller負責呼叫service
