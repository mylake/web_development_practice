# Web 開發最佳實踐

### 溝通
* 遵循: https://github.com/thoughtbot/guides/tree/master/protocol/communication
* 以user story/ticket作為實作的唯一依據，並推動PM及時更新修正user story/ticket
* developer自己認領ticket
* 及時更新ticket狀態
* 積極主動，快速響應，主動push影響自己進度的同事
* 通過screenhero進行遠程溝通

### Git
* 遵循: https://github.com/thoughtbot/guides/tree/master/protocol/git
* 遵循git flow。
* 為每個feature創建merge request 供其他developer review。
* 接受 merge request時要刪除對應的branch。
* 為branch起有意義的名字。
* 一個commit 只會做一件事，避免一個commit做多件事或多個commit做一件事。
* commit message 盡量詳細。
  參考 http://codeinthehole.com/writing/a-useful-template-for-commit-messages/
    1. If applied, this commit will...
    2. Explain why this change is being made
    3. Provide links to any relevant tickets, articles or other resources

### Code Review
* 遵循https://github.com/thoughtbot/guides/tree/master/code-review 。
* merge request 要盡量簡短，以保證能快速的被接受，不阻塞後續的開發。
* merge request 發出之後，要口頭或通過聊天工具通知指定的人，並推動被指定者及時review。
* 及時review別人指定給自己的merge request。
* 及時回應別人的comment，若需新的commit，要及時push並回復告知。

### Docker
* 使用比較知名成熟的base image。
* 將基礎庫和工具放在base image裡。
* 將基礎的系統、軟件設置動作放在base image裡。
* 盡量減少image 的layer。
* 以daemon方式啟動應用程序。
* 將程序相關的配置文件放在image外面，在run container的時候再掛載。
* 將log文件掛載在container 之外。
* 按照時間段分割日誌文件。

### Code Structure
[link](/code.md/)

### Project Manage
* 完整計畫，要包含開發環境的資訊。 要先確認每個人都是在同樣的基準點，沒有認知上的誤差。
* 工作目標, 工作項目, 時間預估

### Rails
------------------------------------
- coding style
  * 遵循ruby-style-guide: https://github.com/bbatsov/ruby-style-guide
  * 遵循rails-style-guide: https://github.com/bbatsov/rails-style-guide
  * 遵循Ruby-Functional-Programming:https://github.com/JuanitoFatas/Ruby-Functional-Programming/blob/master/README-zhCN.md
  * 遵循Better Specs: http://betterspecs.org
  * 遵循git-style-guide: https://github.com/agis-/git-style-guide
- technical stack
  * 用guard作為統一的自動化測試開發環境：bundle exec guard
  * guard-rspec: 根據需要跑rspec。
  * guard-bundler: 根據需要執行bundle install 命令。
  * guard-annotate: 根據需要自動執行annotate來更新各個文件裡的schema info。
  * guard-brakeman: 根據需要自動執行brakeman對code進行安全檢查。
  * guard-rails_best_practices: 根據需要自動執行rails_best_practices對code進行風格檢查。
  * terminal-notifier-guard: 在通知中心顯示各種自動化執行結果。
  * 用最新穩定版的ruby，保證最好的性能和最少的bug。
  * 用spring作為預加載器，避免每次執行rails server/console/rspec/rake等時都要重新加載環境。
  * 多用rubygem而非自己寫code去實現。
  * 優先選用更新頻繁、社區活躍、知名度高的gem。
  * rails的版本升級要小步多走，平滑升級，避免單次大幅度的升級。
  * 將比較費時和實時性要求不要的執行過程交給後台任務去做。
  * 盡量用同一個gem來做延時(delay)或定時(schedule)的後台任務，並在同一個面板中管理。
- code structure
  * 模塊化組織代碼，將相關聯的業務邏輯、功能組織到一個模塊裡，並用namespace和其它模塊區分開來。
  * 版本庫中只保留配置模板settings.example.yml，各個開發人員以模板為基礎加入自己的配置信息生成settings.yml且不提交到版本庫中。
  * 對gem微小的override、extension 放在 lib/gem_name 目錄下，並在config/initializers/gem_name.rb中應用。
  * 合併配置文件，盡量保證只有一個配置文件，便於維護和ops部署時替換配置信息。
  * 在開發早期生產足夠多，盡量真實的數據來支撐測試。為每個model的seed都放在單獨的文件裡並存放在db/seeds/{order}_{model_name}s.rb，然後在db/seeds.rb中按文件名require。
  * 嘗試將項目中比較成熟的功能模塊開源出來，發佈到github，並打包成gem發佈到 rubygems.org。
  * 不斷跟踪rails、ruby的發展進度，並將滿足條件的新的feature、bugfix應用到項目中ãA

### Javascript
------------------------------------
- coding style
  * 遵循Airbnb JavaScript Style Guide: https://github.com/airbnb/javascript
  * 遵循git-style-guide: https://github.com/agis-/git-style-guide
- technical stack
  * Single Page Application + Restful API 架構，實現數據跟UI分開。
  * 用ES6版本javascript編寫code，然後用babel編譯。
  * 用npm進行包管理。
  * 用Webpack打包app，以實現所有資源文件都用統一的方式使用。
  * 用eslint規則審查代碼。
  * 用webpack-dev-server
  * 只import需要的文件，保證打包後的文件最小話。
  * 用webpack-dev-server 作為實時編譯服務器。
  * 多用npm package而非自己寫code去實現。
  * 優先選用更新頻繁、社區活躍、知名度高的plugin。
- code structure
  * 用react-starter-kit 作為項目模板，並保持同步, 模塊化組織代碼，將相關聯的業務邏輯、功能組織到一個模塊裡，並用目錄和其他模塊區分開。
  * 版本庫中只保留配置模板config.example.json，各個開發人員以模板為基礎加入自己的配置信息生成config.json且不提交到版本庫中。
  * 嘗試將項目中比較成熟的功能模塊開源出來，發佈到github，並打包成package發佈到npmjs.org。
  * 不斷跟踪React及其生態鏈的發展進度，並將滿足條件的新的東西應用到項目中。
