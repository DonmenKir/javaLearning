# Java 職訓課程學習筆記索引 (Day 1 - Day 26)

本專案紀錄了從 Java 基礎語法、物件導向核心、進階應用，到 JDBC 資料庫串接與 MVC 架構實作的完整學習歷程。

---

## 📚 目錄 (Table of Contents)

### [Part 1: 語言基礎 (Day 1 - Day 3)](./Day1-15.md)
* **Day 1**: Java 程式結構 (`class`, `main`)、標準輸出 (`System.out.println`)。
* **Day 2**: 變數、八大基本資料型態、型別晉升 (Promotion)、運算子。
* **Day 3**: 流程控制 (`if`, `switch`)、迴圈 (`for`, `while`)、Scanner 輸入。

### [Part 2: 物件導向核心 (Day 4 - Day 6)](./Day1-15.md)
* **Day 4**: 巢狀迴圈邏輯、類別定義初探。
* **Day 5**: 物件實體化 (`new`)、建構子 (Constructor)、`this` 關鍵字。
* **Day 6**: 封裝 (Encapsulation)、Getter/Setter、資料驗證。

### [Part 3: 進階應用 (Day 7 - Day 9)](./Day1-15.md)
* **Day 7**: Swing 視窗程式設計、事件監聽 (Listener)、資料轉型。
* **Day 8**: `static` 關鍵字 (類別層級 vs 物件層級)、Math 工具類別。
* **Day 9**: 陣列 (Array)、記憶體傳址 (Pass by Reference)、物件陣列。

### [Part 4: 繼承與多型 (Day 10 - Day 11)](./Day1-15.md)
* **Day 10**: 繼承 (Inheritance)、Is-A 關係、建構子呼叫順序。
* **Day 11**: 多型 (Polymorphism)、`super` 關鍵字、方法覆寫 (Override)、轉型 (Casting)。

### [Part 5: 抽象與介面 (Day 12 - Day 13)](./Day1-15.md)
* **Day 12**: 抽象類別 (`abstract class`)、`final` 關鍵字。
* **Day 13**: 介面 (`interface`)、多重實作、Java 8 介面新特性 (`default`, `static`)。

### [Part 6: 例外處理 (Day 14 - Day 15)](./Day1-15.md)
* **Day 14**: 例外處理機制 (`try-catch-finally`)、例外階層。
* **Day 15**: `throw` vs `throws`、自訂例外 (Custom Exception)、斷言 (`assert`)。

### [Part 7: 專案實作回顧 (Day 16)](./Day16-30.md)
* **Day 16**: 專案架構討論、MVC 模式複習、程式碼重構 (Refactoring)。

### [Part 8: 進階語法特性 (Day 17 - Day 18)](./Day16-30.md)
* **Day 17**: 內部類別 (Inner Class)、列舉 (Enum)。
* **Day 18**: 匿名內部類別、Lambda 表達式、方法參考 (Method Reference)。

### [Part 9: 集合框架與資料 I/O (Day 19 - Day 21)](./Day16-30.md)
* **Day 19**: 集合框架 (List, Set, Map, Queue)、泛型、Comparable 排序。
* **Day 20**: 檔案 I/O (`File`, `Stream`, `Reader/Writer`)、物件序列化 (`Serializable`)。
* **Day 21**: I/O 與 GUI 整合實戰、多執行緒 (Multithreading) 基礎。

### [Part 10: (此部分與 Part 9 合併，為 Day 21 的進階應用)](./Day16-30.md)
*(註：Day 21 內容較多，包含 I/O、JDBC 初步與執行緒，已整合至 Part 9 或 Part 11 的前導)*

### [Part 11: JDBC 與 MVC 架構基礎 (Day 22 - Day 24)](./Day16-30.md)
* **Day 22**: JDBC 連線 (`DriverManager`, `Connection`)、CRUD 基礎操作。
* **Day 23**: 查詢結果集 (`ResultSet`)、DAO (Data Access Object) 模式入門。
* **Day 24**: 完整 MVC 架構實作 (Student 專案：Model-View-Controller-DAO)。

### [Part 12: 進階 MVC 專案與 SQL 關聯 (Day 25 - Day 26)](./Day16-30.md)
* **Day 25**: 訂單系統 (Gorder) 實戰、多視窗切換與資料傳遞、部分更新 (Partial Update)。
* **Day 26**: SQL 語法精通 (DDL, DML, DQL)、進階查詢 (`LIKE`, `GROUP BY`, `HAVING`)。

---

## 🛠️ 技術堆疊 (Tech Stack)
- **Language**: Java SE (JDK 8+)
- **Database**: MySQL 8.0
- **GUI Framework**: Java Swing
- **Architecture**: MVC (Model-View-Controller), DAO Pattern
- **Tools**: Eclipse, MySQL Workbench

## 📌 學習重點總結
1.  **物件導向 (OOP)**：從封裝、繼承到多型，建立穩固的軟體設計思維。
2.  **資料結構**: 熟練運用 List, Set, Map 處理不同型態的資料集合。
3.  **資料持久化**: 透過 File I/O 與 JDBC 技術，將資料保存至檔案或資料庫。
4.  **架構設計**: 學習 MVC 分層架構，將介面、邏輯與資料存取分離，提升程式碼的可維護性。