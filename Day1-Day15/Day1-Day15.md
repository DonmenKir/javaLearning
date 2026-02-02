# Java學習筆記

# Part 1: Java 語言基礎 (Day 1 - Day 3)

---

## Day 1: Java 程式結構與基礎輸出

### 1. 核心觀念 (Key Concepts)
- **類別 (Class)**：Java 程式的最小單位。
    - **規則**：所有的程式碼都必須定義在 `class` 大括號內。若宣告為 `public class`，檔名必須與類別名稱完全一致（包含大小寫）。
- **主程式入口 (Main Method)**：`public static void main(String[] args)` 是 JVM 啟動程式的唯一入口。
- **輸出串流 (Output Stream)**：
    - `System.out.println()`：印出內容並自動換行。
    - `System.out.print()`：印出內容但不換行。
- **資料型態直覺**：
    - 數值：直接寫數字 (e.g., `10`)，可運算。
    - 字串：用雙引號包覆 (e.g., `"10"`)，視為文字。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **檔名不一致**：類別名 `Ex1` 但檔名存成 `ex1.java` 會導致編譯失敗。
- **分號遺漏**：Java 每個指令結束都要加 `;`。
- **括號對應**：`{}` 與 `()` 必須成對。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `class Name { }` | 定義類別區塊 |
| `public static void main(String[] args)` | 程式執行入口 |
| `System.out.println(val)` | 標準輸出 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Ex1.java, Ex2.java)**：

```java
// Class 名稱必須與檔名相同 (Day1_Practice.java)
class Day1_Practice {
    // 程式入口點
    public static void main(String[] args) {
        // [Ex1] 基礎字串輸出
        // 雙引號包起來的內容被視為字串 (String)
        System.out.println("hello java");

        // [Ex2] 資料型態直覺：數值 vs 字串
        // 1. 數值運算：編譯器辨識為 int，執行加法
        System.out.println(10 + 20);   // 輸出: 30
        
        // 2. 字串文字：編譯器辨識為 String，原樣印出
        System.out.println("10+20");   // 輸出: 10+20
    }
}
```

---

## Day 2: 變數、資料型態與運算子

### 1. 核心觀念 (Key Concepts)
- **基本資料型態 (Primitive Data Types)**：
    - **整數**：`byte` (8-bit), `short` (16-bit), `int` (32-bit, 預設), `long` (64-bit)。
    - **浮點數**：`float` (32-bit, 需加 f), `double` (64-bit, 預設)。
    - **字元**：`char` (16-bit Unicode)。
    - **布林**：`boolean` (true/false)。
- **型別晉升 (Type Promotion)**：在進行算術運算時，`byte`、`short`、`char` 會自動提升為 `int` 以符合 CPU 運算架構。
- **字串串接優先級**：`+` 運算子具有多型性。遇到字串前是「數學加法」，遇到字串後變成「字串串接」，運算方向為「由左至右」。
- **跳脫字元 (Escape Character)**：`\t` (Tab), `\n` (換行), `\"` (雙引號)。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **byte 運算陷阱**：`byte a=1, b=2; byte c=a+b;` ❌ 錯誤，因為 `a+b` 結果是 `int`。必須強制轉型 `(byte)(a+b)`。
- **float 宣告**：`float f = 3.14;` ❌ 錯誤，3.14 預設是 double。必須寫成 `3.14f`。
- **字串串接誤區**：`"10+20=" + 10 + 20` 結果是 `10+20=1020`。若要先加總需加括號 `(10+20)`。
- **遞增/遞減**：`x++` (先賦值再加) vs `++x` (先加再賦值) 的順序差異。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `byte`, `short`, `int`, `long` | 整數宣告 |
| `float f = 1.0f;` | 浮點數宣告 (務必加 f/F) |
| `char c = 'A';` | 字元宣告 (單引號) |
| `boolean b = true;` | 布林宣告 |
| `(type)value` | 強制轉型 (Casting) |
| `+`, `-`, `*`, `/`, `%` | 算術運算子 (`%`取餘數) |
| `+=`, `-=`, `*=`, `/=` | 複合指派運算子 |
| `++`, `--` | 遞增/遞減運算子 |
| `&&`, `\|\|`, `^`, `!` | 邏輯運算子 (And, Or, Xor, Not) |
| `>`, `<`, `>=`, `<=`, `==`, `!=` | 關係運算子 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Ex1 ~ Ex9 所有語法)**：

```java
class Day2_All_In_One {
    public static void main(String[] args) {
        // [Ex1] 字串串接優先級
        // 遇到字串前是數學運算，遇到後變串接
        System.out.println(10 + 20 + "30");       // 3030
        System.out.println("10+20=" + 10 + 20);   // 10+20=1020
        System.out.println("10+20=" + (10 + 20)); // 10+20=30 (括號改變優先權)

        // [Ex2] 型別晉升與強制轉型
        byte b1 = 10, b2 = 20;
        // byte b3 = b1 + b2; // 編譯錯誤: int cannot convert to byte
        int i1 = b1 + b2;     // 正確：用大容器 int 接收
        byte b3 = (byte)(b1 + b2); // 正確：強制轉回 byte
        short s1 = 130; // short 範圍大於 byte

        // [Ex3] 基本型態宣告細節 & 跳脫字元
        float f1 = 30.12f;       // float 必加 f 或 F
        double d1 = 30.12;       // double 為預設浮點數
        char c1 = '巨';          // char 支援 Unicode 中文
        char c2 = 66;            // char 也可存 ASCII 碼 (66 = 'B')
        boolean bool = true;     // 只能是 true 或 false
        String str = "Hello\tJava\nNextLine"; // \t:Tab, \n:換行

        // [Ex4] 變數命名規則
        int $money = 100; // 可以 $ 開頭
        int _score = 90;  // 可以 _ 開頭
        int 國文 = 60;    // 支援中文變數名
        // int 1x = 10;   // 錯誤：不能數字開頭

        // [Ex5, Ex6] 算術與複合指派
        int x = 10;
        x += 5; // 等同 x = x + 5 (15)
        System.out.println(10 / 3);       // 3 (整數除法，無條件捨去小數)
        System.out.println((double)10/3); // 3.333... (將其中一個轉為 double 即可得小數)
        System.out.println(10 % 3);       // 1 (取餘數 Modulus)

        // [Ex7] 遞增運算 (Increment)
        int a = 10;
        int b = ++a; // 前置：a先加1 (a=11)，再給b (b=11)
        int c = a++; // 後置：a先給c (c=11)，a再加1 (a=12)

        // [Ex8, Ex9] 關係與邏輯運算
        int chi = 65, eng = 85;
        // 關係運算回傳 boolean
        System.out.println("chi>60: " + (chi > 60)); 
        
        // 邏輯運算
        System.out.println(chi > 60 && eng > 80); // AND (且): 兩者皆真為真 -> true
        System.out.println(chi > 60 || eng > 80); // OR (或): 一者為真即真 -> true
        System.out.println(chi > 60 ^ eng > 80);  // XOR (互斥): 兩者相異為真 -> false (因兩者皆真)
        System.out.println(!(chi > 60));          // NOT (非): 反轉結果 -> false
        
        // [補充] 位元運算 vs 邏輯運算
        // & 可做位元運算，也可做邏輯運算 (但不具備短路特性 Short-circuit)
        System.out.println(5 & 2); // 0101 & 0010 = 0000 (0)
    }
}
```

---

## Day 3: 流程控制與輸入

### 1. 核心觀念 (Key Concepts)
- **Scanner 類別**：Java 的標準輸入工具，需匯入 `java.util.Scanner`。
- **流程控制 (Flow Control)**：
    - **條件判斷**：`if-else` (區間判斷), `switch` (數值/字串判斷), 三元運算子。
    - **迴圈**：`for` (已知次數), `while` (前測), `do-while` (後測，至少做一次)。
- **跳轉控制 (Jump Statements)**：
    - `break`：完全跳出迴圈。
    - `continue`：跳過本次，直接進入下一圈。
    - `Label`：配合 `break` 跳出指定的多層巢狀迴圈。
- **位元運算 (Bitwise Operators)**：針對整數的二進位進行操作 (`<<`, `>>`, `~`, `&`, `|`)。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **Switch 穿透 (Fall-through)**：`case` 區塊結束若忘記寫 `break`，程式會繼續往下執行下一個 `case` 的內容。
- **Do-While 分號**：`do { ... } while(condition);` 的結尾分號不能省。
- **位元 vs 邏輯**：
    - `&`：位元 AND (計算數值) 或 不短路邏輯 AND。
    - `&&`：短路邏輯 AND (前面條件為假，就不看後面，效率較高)。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `import java.util.Scanner;` | 匯入套件 |
| `new Scanner(System.in)` | 建立 Scanner 物件 |
| `sc.nextInt()`, `sc.next()` | 輸入整數/字串 |
| `cond ? v1 : v2` | 三元運算子 |
| `if`, `else if`, `else` | 條件判斷 |
| `switch(v) { case: break; }` | 多重選擇 (支援 String) |
| `for(;;) {}` | For 迴圈 |
| `while() {}`, `do {} while();` | While 迴圈 |
| `label:`, `break label;` | 迴圈標籤 |
| `~`, `<<`, `>>`, `>>>`, `&`, `\|`, `^` | 位元運算子 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Ex1 ~ Ex9 所有語法)**：

```java
import java.util.Scanner; // 匯入 Scanner

class Day3_All_In_One {
    public static void main(String[] args) {
        // [Ex1] 位元運算 (Bitwise)
        // 邏輯運算 (回傳 boolean)
        int bx = 60, by = 70;
        System.out.println(bx >= 60 && by >= 80); 
        
        // 位元運算 (回傳 int)
        // 5 (0101) & 2 (0010) = 0000 (0)
        System.out.println("5 & 2 = " + (5 & 2));    
        // 5 (0101) | 2 (0010) = 0111 (7)
        System.out.println("5 | 2 = " + (5 | 2));    
        // 補數運算 (NOT): ~x = -(x+1) => ~2 = -3
        System.out.println("~2 = " + (~2));       
        // 左移: 5 (0101) << 2 = 10100 (20)
        System.out.println("5 << 2 = " + (5 << 2));   
        // 右移: 5 (0101) >> 2 = 0001 (1)
        System.out.println("5 >> 2 = " + (5 >> 2));   

        // [Ex2, Ex3] Scanner 輸入
        Scanner sc = new Scanner(System.in);
        System.out.print("請輸入分數(整數): ");
        int score = sc.nextInt(); // 接收整數
        // String s = sc.next();  // 若要接收字串用這行

        // [Ex5] 三元運算子 (簡化 if-else)
        // 條件 ? 成立回傳值 : 不成立回傳值
        System.out.println(score >= 60 ? "及格" : "不及格");

        // [Ex4] 巢狀 If-Else
        if (score >= 90) {
            System.out.println("A");
        } else if (score >= 60) {
            System.out.println("Pass");
        } else {
            System.out.println("Fail");
        }

        // [Ex6] Switch Case (支援 String)
        System.out.print("輸入等級(a/b): ");
        String level = sc.next();
        switch(level) {
            case "a": 
                System.out.println("VIP"); 
                break; // 必加，否則會穿透執行 case "b"
            case "b": 
                System.out.println("Member"); 
                break;
            default: 
                System.out.println("Error Input");
        }

        // [Ex7, Ex8] 迴圈控制 (For, While, Do-While)
        // for: 已知次數
        for(int i = 1; i <= 10; i++) {
            if(i == 3) continue; // continue: 跳過本次 (不印 3)
            if(i == 5) break;    // break: 直接結束迴圈 (只印到 4)
            System.out.print(i + " ");
        }
        System.out.println();
        
        // do-while: 後測迴圈，保證至少做一次
        int j = 10;
        do {
            System.out.println("至少執行一次 (j=" + j + ")");
        } while(j < 5); // 注意分號

        // [Ex9] 巢狀迴圈與 Label (標籤)
        System.out.println("九九乘法表 (遇到2*2全跳出):");
        outer: // 定義標籤指向外層迴圈
        for(int x = 1; x <= 9; x++) {
            for(int y = 1; y <= 9; y++) {
                if(y == 5) break;       // 一般 break: 僅跳出內層
                if(x == 2 && y == 2) break outer; // 帶標籤 break: 直接跳出外層
                System.out.print(x + "*" + y + "\t");
            }
            System.out.println();
        }
    }
}
```

# Part 2: 物件導向核心 (Day 4 - Day 6)

---

## Day 4: 巢狀迴圈邏輯與類別初探

### 1. 核心觀念 (Key Concepts)
- **巢狀迴圈 (Nested Loops)**：迴圈結構內部包含另一個迴圈。
    - **時鐘原理**：外層迴圈像「時針」，內層迴圈像「分針」。
    - **執行頻率**：外層跑 1 次，內層就要跑完一整輪。
- **變數範疇 (Scope)**：變數只在宣告它的 `{ }` 區塊內有效（區域變數）。
- **類別定義 (Class Definition)**：
    - 類別是物件的**藍圖 (Blueprint)**。
    - 定義物件擁有的**屬性 (Fields)**，也就是成員變數。
    - Day 4 階段僅定義資料結構，尚未實作方法。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **迴圈變數衝突**：內外層迴圈變數名稱不能相同（通常外層用 `i` 或 `x`，內層用 `j` 或 `y`）。
- **標籤位置**：標籤 `label:` 必須緊貼在迴圈上方。
- **類別 vs 物件**：寫好 `class` 只是畫好設計圖，必須在 `main` 方法中雖然宣告變數但還沒 `new` 時，是無法使用的（雖然 Day 4 還沒教到 new，但觀念先建立）。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `for(int i=0; i<n; i++){ for... }` | 雙層迴圈結構 |
| `class Student { String name; }` | 定義包含屬性的類別 |
| `labelName:` | 定義標籤 (Label) |
| `break labelName;` | 跳出指定標籤的迴圈 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Ex1.java, student.java, add1.java)**：

```java
// [Ex1.java] 巢狀迴圈邏輯與標籤展示
class Day4_Loop_Demo {
    public static void main(String[] args) {
        String str = "";
        
        // z: // 標籤定義 (Label)
        // 外層迴圈 (x): 0, 1, 2 (共3次)
        for(int x = 0; x < 3; x++) {
            // 內層迴圈 (y): 0, 1 (每輪2次)
            for(int y = 0; y < 2; y++) {
                // if(x==1) break; // 一般 break: 跳出內層 y 迴圈
                // if(x==2) break z; // 標籤 break: 直接跳出外層 x 迴圈
                
                // 字串累加，紀錄執行軌跡 (00, 01, 10...)
                str = str + x + y; 
                System.out.println("x=" + x + "\ty=" + y + "\tstr=" + str);
            }
        }
        // 最終字串: 000110112021
        System.out.println(str);
    }
}

// [student.java] 類別定義 (Data Structure)
// 只有屬性 (Field)，沒有方法
class StudentDefinition {
    String sname;
    int chi;
    int eng;
}

// [add1.java] 過程導向 vs 物件導向的前奏
class Add1 {
    public static void main(String[] args) {
        // 在學會物件導向之前，資料是分散的變數，難以管理
        String name1 = "auu";
        int chi1 = 65;
        // ... (省略繁瑣變數)
        System.out.println("名:" + name1 + "\t國文:" + chi1);
    }
}
```

---

## Day 5: 建構子與物件初始化

### 1. 核心觀念 (Key Concepts)
- **物件實體化 (Instantiation)**：使用 `new` 關鍵字在 Heap Memory (堆積記憶體) 中分配空間產生真正的物件。
- **建構子 (Constructor)**：
    - 與類別**同名**，**無回傳型別**（連 `void` 都沒有）。
    - **用途**：物件誕生 (new) 的瞬間自動執行，負責**初始化**。
    - **邏輯**：可以在建構子中進行運算（如 `Order` 類別中自動計算總金額）。
- **關鍵字 `this`**：
    - 代表**當前物件的參考**。
    - 用於區分「成員變數 (Field)」與「區域變數/參數 (Parameter)」。
- **自動裝箱 (AutoBoxing)**：基本型態 (`double`, `int`) 自動轉為包裝物件 (`Double`, `Integer`)。
- **Import 規則**：使用 `java.util.*` 或完整類別名稱來引用其他套件的類別。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **建構子加 void**：若寫成 `void Student() {...}`，Java 會將其視為一般方法，而非建構子。
- **物件比較**：`d1 == d2` 比較基本型態的值；`D1 == D2` 比較物件記憶體位址；`D1.equals(D2)` 比較物件內容值。
- **Import**：`java.lang` 套件下的類別 (如 `Thread`, `String`) 不需 import，其他都需要。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `new ClassName();` | 建立物件實體 |
| `ClassName(args) { ... }` | 定義建構子 |
| `this.field = param;` | 存取當前物件的屬性 |
| `Integer`, `Double` | 包裝類別 (Wrapper Class) |
| `import java.util.Scanner;` | 匯入套件 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Order.java, Student.java, Ex1.java, Ex2.java, AddOrder.java)**：

```java
import java.util.Scanner; // [Ex1] 匯入範例
import java.util.Date;

class Day5_All_In_One {
    public static void main(String[] args) {
        // [AddOrder.java] 測試建構子邏輯
        // 傳入參數: "一頁書", 3 (尺), 1 (筆) -> 自動計算 sum = 118
        Order o1 = new Order("一頁書", 3, 1);
        o1.show(); 

        // [Add2.java] 測試 Student 建構子與 this
        Student s1 = new Student(80);
        s1.show();

        // [Ex1.java] 絕對路徑與相對路徑寫法
        java.lang.Thread t1 = new java.lang.Thread(); // 絕對路徑
        Date d = new Date(); // 需要 import

        // [Ex2.java] AutoBoxing 與 Wrapper Class
        double d1 = 10.12;      // 基本型態
        Double D1 = 10.12;      // 自動裝箱 (Object)
        Double D2 = 10.12;
        
        System.out.println("值比較(==): " + (d1 == D1));    // true (AutoUnboxing)
        System.out.println("物件位址比較(==): " + (D1 == D2)); // false (不同物件)
        System.out.println("內容比較(.equals): " + D1.equals(D2)); // true (建議用法)
    }
}

// [Order.java] 建構子多載 (Overloading) 與 商業邏輯
class Order {
    String name;
    int ruler, pen, sum; 

    // 建構子 1: 全參數
    Order(String name, int ruler, int pen) {
        if(ruler >= 0 && pen >= 0) {
            this.name = name;      
            this.ruler = ruler;
            this.pen = pen;
            // [商業邏輯] 自動計算總金額
            this.sum = this.ruler * 29 + this.pen * 31;
        }
    }
    // 建構子 2: 少了 name (Overloading)
    Order(int ruler, int pen) {
        if(ruler >= 0 && pen >= 0) {
            this.ruler = ruler;
            this.pen = pen;
            this.sum = this.ruler * 100 + this.pen * 35; // 不同計價邏輯
        }
    }
    void show() {
        System.out.println("名:" + name + "\t成交金額:" + sum);
    }
}

// [Student.java] 建構子與 this
class Student {
    String name;
    int chi;
    double eng;

    Student(int chi) {
        // this.chi 指向 field，chi 指向參數
        this.chi = chi; 
        // System.out.println("新增一位學員");
    }
    void show() {
        System.out.println("名:" + name + "\t國文:" + chi);
    }
}
```

---

## Day 6: 封裝 (Encapsulation)

### 1. 核心觀念 (Key Concepts)
- **封裝 (Encapsulation)**：
    - **隱藏資訊**：將資料 (`fields`) 設為 `private`，防止外部直接存取。
    - **公開介面**：提供 `public` 的方法 (Getter/Setter) 作為存取窗口。
- **存取修飾子 (Access Modifiers)**：
    - `private`：僅限類別內部存取。
    - `public`：完全公開。
- **資料驗證 (Data Validation)**：在 Setter 中加入 `if` 判斷，防止不合理的資料（如負分）進入物件。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **Private 存取**：`s1.chi = -100` 會編譯失敗 (The field is not visible)。
- **Setter 邏輯**：有寫 Setter 但沒寫 `if` 判斷，封裝就沒有意義。
- **方法邏輯混淆**：在方法內修改了屬性（如 `change2`），要清楚是修改了物件的狀態，還是只回傳了運算結果。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `private int x;` | 宣告私有變數 |
| `public void setX(int x)` | 定義公開 Setter |
| `public int getX()` | 定義公開 Getter |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Student.java, AddStudent.java)**：

```java
// [Student.java] 完整封裝實作
class Student {
    // 1. 私有化屬性 (Private Fields)
    private String name;
    private int chi = 60; // 預設值
    private int eng, math, sum;

    // 建構子：初始化時也要守住資料規則
    Student(String name, int chi, int eng, int math) {
        if(chi >= 0 && chi <= 100 && eng >= 0 && eng <= 100) {
            this.name = name;
            this.chi = chi;
            this.eng = eng;
            this.math = math;
            this.sum = chi + eng + math; // 連動計算
        } else {
            System.out.println("分數需介於0~100");
        }
    }

    // 2. 公開 Setter (Public Setter) - 寫入入口
    public void setChi(int chi) {
        // [資料驗證] 守門員
        if(chi >= 0 && chi <= 100) {
            this.chi = chi;
            // 若需連動: this.sum = this.chi + this.eng + this.math;
        } else {
            System.out.println("分數需介於0~100 (無效輸入)");
        }
    }
    
    // [Student.java] 商業邏輯方法
    // 模擬改變分數並回傳總分，同時修改了物件狀態
    int change2(int chi, int eng, int math) {
        this.chi = chi;
        this.eng = eng;
        this.math = math;
        return chi + eng + math;
    }

    // 3. 公開 Getter (Public Getter) - 讀取出口
    public int getChi() { return this.chi; }
    public String getName() { return this.name; }

    void show() {
        System.out.println("名:" + name + "\t國文:" + chi + "\t總分:" + sum);
    }
}

// [AddStudent.java] 測試封裝與方法
class Day6_Demo {
    public static void main(String[] args) {
        Student s1 = new Student("a", 78, 98, 65);
        Student s2 = new Student("b", 68, 88, 65);

        // 測試邏輯方法
        s1.change2(85, 65, 100);
        
        // s1.chi = -100; // [編譯錯誤] private 不可見
        
        // 透過 Setter 嘗試設定無效值
        s1.setChi(-100); // 輸出警告，數值不變
        
        System.out.println("s1的名:" + s1.getName());
        System.out.println("s1的國文:" + s1.getChi()); 
        s1.show();
    }
}
```
# Part 3: 進階應用 (Day 7 - Day 9)

---

## Day 7: 視窗程式設計 (Swing GUI)

### 1. 核心觀念 (Key Concepts)
- **Swing 框架**：Java 的圖形使用者介面 (GUI) 函式庫。
    - **結構**：`JFrame` (視窗) -> `JPanel` (畫布) -> 元件 (`JButton`, `JTextField`, `JLabel`, `JTextArea`)。
- **事件驅動程式設計 (Event-Driven Programming)**：程式的執行流程由使用者的操作 (點擊、輸入) 來觸發，而非由上而下線性執行。
- **監聽器 (Listener)**：負責「監聽」事件的介面。例如 `MouseListener` 監聽滑鼠動作 (Click, Press, Release)。
- **匿名內部類別 (Anonymous Inner Class)**：用於快速實作介面 (如 `new MouseAdapter() {...}`)，直接在按鈕加入監聽器時定義行為。
- **資料轉型 (Parsing)**：GUI 輸入框 (`JTextField`) 的內容永遠是 `String`。若要進行數學運算，必須先轉型 (e.g., `Integer.parseInt`)。
- **MVC 雛形**：將 **View** (OrderUI 負責顯示與輸入) 與 **Model** (Order 負責資料儲存與邏輯計算) 分離。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **忘記轉型**：直接拿 `getText()` 的內容去減法 (`"10" - "5"`)，會導致編譯錯誤。字串不能直接減法。
- **匿名內部類別語法**：`new MouseAdapter() { ... }` 的語法結構較複雜，括號容易配對錯誤。
- **邏輯混雜**：把計算總金額的公式寫在 UI 的按鈕事件裡，而不是封裝在 `Order` 物件中（違反 OOP 封裝原則）。
- **主要類別**：Swing 程式通常由 `UiTest` 或 `OrderUI` 啟動，而非資料類別。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `extends JFrame` | 繼承視窗類別，使類別成為一個視窗 |
| `btn.addMouseListener(...)` | 為按鈕加入滑鼠事件監聽器 |
| `new MouseAdapter(){...}` | 匿名內部類別 (實作監聽器介面) |
| `input.getText()` | 取得輸入框 (`JTextField`) 的文字 |
| `output.setText(str)` | 設定顯示元件 (`JLabel`, `JTextArea`) 的文字 |
| `Integer.parseInt(str)` | 將字串轉為整數 (重要!) |
| `new Integer(str)` | (舊式) 建立整數物件 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 UiTest.java, OrderUI.java, Order.java)**：

```java
import javax.swing.*;
import java.awt.event.*;
import java.awt.*;

// [UiTest.java] 基礎 GUI 練習
class UiTest extends JFrame {
    private JPanel contentPane;
    private JTextField input;

    // 建構子：設定視窗
    public UiTest() {
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); // 關閉時結束程式
        setBounds(200, 100, 395, 476); // 位置與大小
        contentPane = new JPanel();
        setContentPane(contentPane);
        contentPane.setLayout(null); // 絕對佈局

        // 加入標籤
        JLabel lbl = new JLabel("學生成績");
        lbl.setBounds(113, 10, 73, 30);
        contentPane.add(lbl);

        // 加入輸入框
        input = new JTextField();
        input.setBounds(96, 31, 123, 28);
        contentPane.add(input);
    }
    
    public static void main(String[] args) {
        // 啟動視窗
        new UiTest().setVisible(true);
    }
}

// [OrderUI.java] 進階 GUI 與事件處理 (View)
class OrderUI extends JFrame {
    private JTextField name, lcd, ram, mouse;
    private JCheckBox member; // 核取方塊
    private JTextArea output; // 多行文字區

    public OrderUI() {
        // ... (省略視窗設定與排版程式碼，與上面類似) ...
        
        JButton btn = new JButton("確定");
        // [關鍵] 加入滑鼠監聽器
        btn.addMouseListener(new MouseAdapter() {
            @Override
            public void mouseClicked(MouseEvent e) {
                // 1. 擷取輸入 (Harvesting)
                String Name = name.getText();
                String Lcd = lcd.getText();
                String Ram = ram.getText();
                String Mouse = mouse.getText();

                // 2. 資料轉型 (Parsing)
                // 必須轉成 int 才能做比較與運算
                // 注意: 若輸入非數字會拋出 NumberFormatException (Day 14 會教如何處理)
                int LCD = Integer.parseInt(Lcd);
                int RAM = Integer.parseInt(Ram);
                int MOUSE = Integer.parseInt(Mouse);

                // 3. 邏輯檢查與物件互動 (Interaction)
                if(LCD >= 0 && RAM >= 0 && MOUSE >= 0) {
                    // 建立 Order 物件 (Model)，將資料傳入
                    // member.isSelected() 回傳 boolean
                    Order o = new Order(Name, LCD, RAM, MOUSE, member.isSelected());
                    
                    // 4. 更新畫面 (Update View)
                    // 呼叫 o.getName(), o.getSum() 等方法
                    output.setText(
                        "name=" + o.getName() + 
                        "\nlcd:" + o.getLcd() + 
                        "\nram:" + o.getRam() + 
                        "\nmouse:" + o.getMouse() + 
                        "\nsum:" + o.getSum() // 取得計算後的總金額
                    );
                } else {
                    output.setText("數量需 >= 0");
                }
            }
        });
        // add(btn); ...
    }
    
    public static void main(String[] args) {
        new OrderUI().setVisible(true);
    }
}

// [Order.java] 資料模型與商業邏輯 (Model)
// 負責單純的計算，不涉及視窗顯示
class Order {
    private String name;
    private int lcd, ram, mouse;
    private double sum;
    private boolean member;

    // 建構子：初始化同時計算總金額
    public Order(String name, int lcd, int ram, int mouse, boolean member) {
        this.name = name;
        this.lcd = lcd;
        this.ram = ram;
        this.mouse = mouse;
        this.member = member;
        
        // 商業邏輯 (Business Logic)
        this.sum = lcd * 4999 + ram * 1280 + mouse * 799;
        
        // 會員打折邏輯
        if(member) {
            this.sum = this.sum * 0.95;
        }
    }

    // Getter 方法供外部讀取結果
    public double getSum() { return sum; }
    public String getName() { return name; }
    public int getLcd() { return lcd; }
    public int getRam() { return ram; }
    public int getMouse() { return mouse; }
}
```

---

## Day 8: Static 關鍵字與 Math 工具

### 1. 核心觀念 (Key Concepts)
- **Static (靜態)**：
    - **類別層級 (Class Level)**：被 `static` 修飾的成員屬於「類別」，而非「個別物件」。
    - **記憶體共享 (Shared Memory)**：所有該類別的物件**共用同一份** `static` 變數。修改一次，全體受影響。
    - **存取限制**：`static` 方法中**不能**使用 `this` (因為沒有物件實體)，只能存取其他的 `static` 成員。
- **工具類別 (Utility Class)**：
    - 如 `java.lang.Math` 或 `Integer`。
    - 方法全為 static，設計目的是為了提供功能，**不需 new 物件**即可直接使用。
    - 通常建構子會設為 private (不讓人 new)。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **this 誤用**：在 `static void main` 或其他 static 方法中寫 `this.variable`，會導致編譯錯誤。
- **實體變數混淆**：誤以為 `static` 變數像普通變數一樣每個物件都有一份。
- **Math 類別使用**：試圖 `new Math()` (錯誤)，應直接用 `Math.pow()`。
- **Wrapper Class**：`new Integer(10)` 是舊式寫法 (Java 9 Deprecated)，建議用 `Integer.valueOf(10)` 或直接賦值 (AutoBoxing)。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `private static int pv;` | 宣告靜態變數 (所有物件共享) |
| `static void method(){}` | 宣告靜態方法 (不需 new 即可呼叫) |
| `ClassName.method()` | 呼叫靜態方法的標準方式 |
| `Math.PI` | 圓周率常數 |
| `Math.E` | 自然對數底數 |
| `Math.pow(a, b)` | 次方運算 ($a^b$)，回傳 double |
| `Math.abs(a)` | 絕對值 |
| `Integer.valueOf(str)` | 將字串轉為 Integer 物件 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Fv.java, Ex1.java, AddFv.java, Ex2.java, Ex3.java)**：

```java
// [Ex1.java] Math 工具與 Wrapper Class
class Day8_Math_Wrapper {
    public static void main(String[] args) {
        // Math 類別方法 (全 static，直接用)
        System.out.println(Math.PI);          // 3.14159...
        System.out.println(Math.abs(-100));   // 100
        // pow 回傳 double
        System.out.println(Math.pow(2, 3));   // 2的3次方 = 8.0
        
        // 複雜運算
        double x = 10.24, y = 45.3;
        System.out.println(Math.pow(x/2.5, y/5.2));

        // Wrapper Class 與 字串轉型
        String sumStr = "1000";
        // 字串串接
        System.out.println(100 + sumStr); // "1001000"
        
        // 轉型成 int (Primitive)
        int sumInt = Integer.parseInt(sumStr);
        System.out.println(100 + sumInt); // 1100 (數值加法)
        
        // 轉型成 Integer (Object)
        Integer sumObj = Integer.valueOf(sumStr);
        System.out.println(100 + sumObj); // 1100 (AutoUnboxing)
    }
}

// [Fv.java] 自訂 Static 邏輯 (財務計算)
class Fv {
    // static 變數：全體共享 (本金)
    // 只要設定一次，所有 Fv 物件都會用到這個本金
    private static int pv; 
    
    // instance 變數：物件獨有 (利率, 期數, 本利和)
    private double r;
    private int n;
    private int fv;

    // 建構子 (初始化物件獨有屬性)
    Fv(double r, int n) {
        this.r = r;
        this.n = n;
        // 計算本利和 (用到 static pv)
        fv = (int)(pv * (1 + r * n));
    }

    // static 方法：設定共享的本金
    // 只能存取 static 變數 pv，不能存取 r, n (因為不知道是哪個物件的 r, n)
    static void setPv(int pv) {
        if(pv >= 0) {
            Fv.pv = pv; // 正確: 透過類別名存取
            // this.pv = pv; // 錯誤: static 方法沒有 this
        }
    }

    // static 方法：工具型方法 (純計算，不依賴物件狀態)
    static int cal(int x, int y) {
        return x * y;
    }
    
    static String companyName() {
        return "巨匠電腦";
    }

    void show() {
        // 重算 fv (若 pv 在中途被改了)
        fv = (int)(pv * (1 + r * n));
        System.out.println("本金:" + pv + "\t利率:" + r + "\t期數:" + n + "\t本利和:" + fv);
    }
}

// [AddFv.java] 測試 Static 行為
class AddFv {
    public static void main(String[] args) {
        // 1. 呼叫 Static 方法 (不需 new)
        System.out.println(Fv.companyName());
        Fv.setPv(10000); // 設定全域本金為 10000
        
        // 2. 建立多個物件 (利率不同)
        Fv f1 = new Fv(0.015, 1);
        Fv f2 = new Fv(0.014, 2);
        
        f1.show(); // 本金 10000
        f2.show(); // 本金 10000 (共享)
        
        System.out.println("====== 修改 Static 變數 ======");
        
        Fv.setPv(20000); // 修改全域本金
        // 再次顯示，所有物件的計算結果都會改變！
        f1.show(); // 本金 20000
        f2.show(); // 本金 20000
    }
}

// [Ex3.java] 陣列基礎 (Array Basics) - 預習 Day 9
class Day8_Array_Preview {
    public static void main(String[] args) {
        // 1. 宣告並配置空間 (預設值為 0)
        int[] x = new int[3]; 
        x[0] = 10;
        x[1] = 20;
        System.out.println(x[0] + "\t" + x[1] + "\t" + x[2]);

        // 2. 宣告並直接初始化值
        int[] x2 = new int[]{10, 20, 15};
        System.out.println(x2[0]);
    }
}
```

---

## Day 9: 陣列進階與記憶體位址

### 1. 核心觀念 (Key Concepts)
- **陣列 (Array)**：
    - 儲存固定大小、同型別資料的容器。
    - 在 Java 中，陣列是**物件 (Reference Type)**。
- **傳址 (Pass by Reference)**：
    - 陣列變數 (如 `x`) 存的是 **Heap 記憶體位址 (Address)**，而非實際數值。
    - `x = y` 意味著將 `y` 的位址複製給 `x`，導致兩者指向**同一個實體**。
    - 修改 `x[0]`，`y[0]` 也會跟著變。
- **垃圾回收 (Garbage Collection, GC)**：當一個物件（如原本的 `x` 陣列）沒有任何變數指向它時，會被視為垃圾並自動回收。
- **多維陣列**：
    - 陣列的陣列。
    - **不規則陣列 (Jagged Array)**：Java 允許二維陣列的每一列 (`Row`) 長度不同。
- **物件陣列 (Array of Objects)**：
    - `Member[] m = new Member[3]` 只是切出 3 個存放「位址」的格子 (預設 null)。
    - **必須**再個別執行 `m[0] = new Member(...)` 才是真正建立物件。
- **增強型迴圈 (Foreach)**：`for(Type var : array)`，用於遍歷陣列，語法簡潔。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **NullPointerException**：宣告了物件陣列 `Member[] m = new Member[3]`，卻忘記 `m[0] = new Member()`，直接呼叫 `m[0].show()` 會崩潰。
- **陣列複製誤區**：以為 `int[] a = b;` 是複製內容 (Backup)，其實只是多了一個別名 (Alias)。
- **索引越界**：存取 `x[3]` 但長度只有 3 (索引 0~2)，會拋出 `ArrayIndexOutOfBoundsException`。
- **Foreach 限制**：Foreach 只能讀取，不能用來修改陣列裡面的值 (因為它操作的是複本)。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `int[] x = new int[3];` | 宣告並配置空間 |
| `int[] x = {1, 2, 3};` | 宣告並初始化 |
| `int[][] x = new int[2][];` | 宣告二維 (不規則) |
| `int[][][] x = new int[2][2][3];` | 三維陣列 |
| `x.length` | 取得陣列長度 (屬性，無括號) |
| `for(int v : x)` | 增強型迴圈 (Foreach) |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Ex2.java, Ex4.java, Ex5.java, Ex6.java, Ex7.java, Add1.java, Add2.java, Add3.java)**：

```java
// [Member.java] 資料類別
class Member {
    private String name;
    private String address;

    Member(String name, String address) {
        this.name = name;
        this.address = address;
    }
    void setName(String name) { this.name = name; }
    String show() { return "名:" + name + "\t地址:" + address; }
}

class Day9_Array_Deep_Dive {
    public static void main(String[] args) {
        // [Ex2] 傳址 (Pass by Reference) 演示
        int[] x = {10, 20, 30};
        int[] y = {40, 50, 60};
        
        System.out.println("x位址:" + x); // 印出記憶體雜湊碼 (e.g., [I@15db9742)
        
        x = y; // [關鍵] 把 y 的位址貼給 x
        // 現在 x 和 y 指向同一個 {40, 50, 60}
        // 原本 x 指向的 {10, 20, 30} 變成垃圾 (GC)
        
        x[0] = 100; // 修改 x
        System.out.println(y[0]); // 輸出: 100 (因為 y 也是指同一個地方)

        // [Ex4, Ex6] 二維陣列與 Foreach
        int[][] matrix = {
            {10, 20, 30},
            {40, 50, 60, 70}, // 不規則長度
            {80, 90}
        };

        // 傳統迴圈遍歷
        for(int i=0; i<matrix.length; i++) {
            System.out.print("Row " + i + ": ");
            for(int j=0; j<matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }

        // Foreach 迴圈遍歷 (更簡潔)
        for(int[] row : matrix) {      // 取出每一列 (int[])
            for(int val : row) {       // 取出列中的值 (int)
                System.out.print(val + " ");
            }
            System.out.println();
        }

        // [Ex7] 三維陣列 (概念)
        int[][][] cube = new int[2][2][3];
        cube[0][0][0] = 999;
        // 遍歷需要三層迴圈

        // [Add1.java] 物件參考操作
        Member m1 = new Member("a", "台北");
        Member m2 = new Member("b", "高雄");
        // m1 = m2; // m1 指向 m2 的物件
        // m1 = null; // 切斷連結，m1 不指向任何物件
        // System.out.println(m1.show()); // 若 m1 為 null，這裡會報錯

        // [Add2.java, Add3.java] 物件陣列初始化 (最重要!)
        System.out.println("=== 物件陣列 ===");
        
        // 1. 宣告陣列容器 (此時裡面全是 null)
        Member[] members = new Member[3]; 
        
        // 2. [關鍵] 必須個別建立物件 (Instantiate)
        members[0] = new Member("a1", "Taipei");
        members[1] = new Member("a2", "Taipei");
        members[2] = new Member("a3", "Taipei");

        // 另一種初始化寫法
        Member[] members2 = new Member[] {
            new Member("b1", "Tainan"),
            new Member("b2", "Kaohsiung")
        };

        // 二維物件陣列
        Member[][] group = new Member[2][];
        group[0] = new Member[2]; // 第一組 2 人
        group[1] = new Member[3]; // 第二組 3 人
        
        group[0][0] = new Member("Leader", "Taipei"); // 填入資料

        // 遍歷物件陣列
        for(Member m : members) {
            // 若陣列中有 null (例如宣告長度3但只填2個)，這裡可能會報錯
            // if(m != null) 
            System.out.println(m.show());
        }
    }
}
```
# Part 4: 繼承與多型 (Day 10 - Day 11)

---

## Day 10: 繼承入門 (Inheritance)

### 1. 核心觀念 (Key Concepts)
- **繼承 (Inheritance)**：
    - 物件導向程式設計 (OOP) 的核心機制。
    - 允許一個類別 (子類別/Subclass) 繼承另一個類別 (父類別/Superclass) 的屬性與方法。
    - **目的**：減少重複代碼 (Code Reuse)、建立類別階層 (Hierarchy)。
- **Is-A 關係 (Is-A Relationship)**：
    - 繼承代表「是一種」的關係。
    - 例如：`class A extends School`，代表 `A` **是** 一種 `School`。
- **建構子呼叫順序 (Constructor Chaining)**：
    - 建立子類別物件時，會**先執行父類別的建構子**，再執行子類別的建構子。
    - 這是為了確保父類別的屬性先被初始化。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **多重繼承**：Java 的類別**不支援**多重繼承 (`extends A, B` 是錯的)，只能繼承一個父類別。但可以實作多個介面。
- **私有成員存取**：父類別的 `private` 成員雖然被繼承了，但子類別**無法直接存取**，必須透過父類別的 `public` 方法 (如 Getter/Setter)。
- **建構子不繼承**：子類別不會繼承父類別的建構子，但會呼叫它。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `class Child extends Parent` | 定義繼承關係 |
| `super()` | (隱式) 在子類別建構子第一行，呼叫父類別無參數建構子 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 School.java, A.java, B.java, Add1.java, Add2.java)**：

```java
// [School.java] 父類別 (Superclass)
class School {
    String name = "guest";
    int chi;

    // 父類別建構子
    School() {
        // System.out.println("School init");
    }
}

// [A.java] 子類別 (Subclass)
// A 繼承 School，自動擁有 name 和 chi
class A extends School {
    int word; // A 擴充的屬性

    void show() {
        // 可以直接使用繼承自父類別 School 的 name 和 chi
        System.out.println("名:" + name + "\tchi:" + chi + "\tword:" + word);
    }
}

// [B.java] 另一個子類別
class B extends School {
    int excel;

    void show() {
        System.out.println("名:" + name + "\tchi:" + chi + "\texcel:" + excel);
    }
}

// [Add1.java] 測試繼承
class Day10_Inheritance_Demo {
    public static void main(String[] args) {
        // 1. 建立子類別物件
        A a1 = new A(); 
        
        // a1 is-a A, a1 is-a School
        // a1 has-a word (自己的)
        // a1 has-a name (繼承的)
        
        a1.name = "Andy";
        a1.word = 100;
        a1.show(); // 呼叫 A 的方法

        B b1 = new B();
        b1.name = "David";
        b1.excel = 90;
        b1.show();
    }
}

// [Company.java] 另一個繼承範例 (員工系統)
class Company {
    String name;
    String address;

    Company(String name) {
        this.name = name;
        System.out.println("新增一位員工,名=" + name);
    }
    
    // 多載建構子
    Company(String name, String address) {
        this.name = name;
        this.address = address;
        System.out.println("新增員工=" + name + "\t地址=" + address);
    }
}

// [Ca.java] Company 的子類別
class Ca extends Company {
    int lcd;

    // 子類別建構子
    Ca(String name) {
        super(name); // 呼叫父類別建構子
        System.out.println("Ca部門的人");
    }

    Ca(String name, String address, int lcd) {
        super(name, address); // 指定呼叫父類別雙參數建構子
        this.lcd = lcd;
        System.out.println("Ca 部門的人 lcd=" + lcd);
    }
}

// [Add2.java, Add3.java] 測試 Company 繼承體系
class Day10_Company_Demo {
    public static void main(String[] args) {
        Company c1 = new Company("Boss"); // 父類別物件
        Ca c2 = new Ca("Employee", "Taipei", 10); // 子類別物件
        
        // 子類別物件可以存取父類別屬性 (若非 private)
        System.out.println(c2.name);
        System.out.println(c2.lcd);
    }
}
```

---

## Day 11: 多型與 Super (Polymorphism & Super)

### 1. 核心觀念 (Key Concepts)
- **多型 (Polymorphism)**：
    - 使用**父類別的變數**來操作**子類別的物件**。
    - **口訣**：宣告父類別，建立子類別 (Declare Parent, Instantiate Child)。
        - `Parent p = new Child();`
    - **效益**：程式碼可以針對「父類別」寫，就能通吃所有「子類別」，極大增加擴充彈性 (如陣列存不同子物件)。
- **Super 關鍵字**：
    - `super(args)`：明確呼叫父類別的特定建構子 (必須在第一行)。
    - `super.method()`：呼叫父類別被覆寫掉的方法。
- **方法覆寫 (Overriding)**：
    - 子類別重新定義父類別的方法 (名稱、參數、回傳值必須完全相同)。
    - 多型運作時，會執行**子類別覆寫後**的版本 (動態繫結)。
- **轉型 (Casting)**：
    - **Upcasting** (向上轉型)：`Order o = new A();` (自動)。把子類別當父類別看。
    - **Downcasting** (向下轉型)：`((A)o).showA();` (強制)。把父類別看回子類別，才能使用子類別特有功能。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **方法可見度**：覆寫方法時，子類別的權限不能比父類別嚴格 (e.g., 父 `public`，子不能 `protected`)。
- **父類別變數限制**：`Order o = new A();`，雖然 `o` 實際上是 `A`，但透過 `o` 只能呼叫 `Order` 裡定義過的方法。若要呼叫 `A` 獨有的方法，必須轉型。
- **轉型失敗**：如果 `o` 其實是 `B` 物件，卻硬要轉成 `A` (`(A)o`)，執行時會拋出 `ClassCastException`。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `super(name);` | 呼叫父類別建構子 |
| `super.method()` | 呼叫父類別方法 |
| `Order o = new A();` | 多型宣告 |
| `@Override` | (建議) 標註方法覆寫 |
| `((Type)obj).method()` | 強制轉型後呼叫方法 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Student.java, Sa.java, Sb.java, Add1.java, Order.java, A.java, B.java, C.java, Add2.java, Add3.java)**：

```java
// [Student.java] 父類別
class Student {
    private String name;
    
    Student(String name) {
        this.name = name;
    }
    
    String show() {
        return "名:" + name;
    }
    
    // 預留給子類別覆寫的方法
    void skill() {
        System.out.println("Student skill");
    }
}

// [Sa.java] 子類別，示範 super 與 overriding
class Sa extends Student {
    private int chi;

    Sa(String name, int chi) {
        super(name); // [關鍵] 呼叫父類別 Student(String name) 建構子初始化 name
        this.chi = chi; // 初始化自己的屬性
    }
    
    // 方法覆寫 (Overriding)
    String show() {
        // 呼叫父類別原本的 show()，再加上自己的資訊
        return super.show() + "\t國文:" + chi;
    }
    
    // 獨有方法
    void skillA() {
        System.out.println("A skill");
    }
}

// [Sb.java] 另一個子類別
class Sb extends Student {
    private int eng;
    Sb(String name, int eng) {
        super(name);
        this.eng = eng;
    }
    String show() {
        return super.show() + "\t英文:" + eng;
    }
}

// [Add1.java] 測試繼承與覆寫
class Day11_Inheritance_Test {
    public static void main(String[] args) {
        Sa s1 = new Sa("Andy", 12);
        Sb s2 = new Sb("David", 23);
        
        System.out.println(s1.show()); // 執行 Sa 的 show
        System.out.println(s2.show()); // 執行 Sb 的 show
    }
}

// ===== 多型範例 (Order 體系) =====

// [Order.java] 父類別
class Order {
    private String name;
    Order(String name) { this.name = name; }
    
    String show() { return "名:" + name; }
    void showOrder() { System.out.println("Order skill"); }
    
    // 為了多型方便，有時會在父類別預留空方法 (或用抽象方法 Day12)
    void setLcd(int lcd) {} 
}

// [A.java] Order 的子類別
class OrderA extends Order {
    private int lcd;
    OrderA(String name, int lcd) {
        super(name);
        this.lcd = lcd;
    }
    // 覆寫 setLcd
    void setLcd(int lcd) { this.lcd = lcd; }
    
    String show() { return super.show() + "\tlcd:" + lcd; }
    void showA() { System.out.println("A skill"); }
}

// [B.java, C.java 類似 OrderA，略]

// [Add2.java] 轉型 (Casting) 測試
class Day11_Casting_Test {
    public static void main(String[] args) {
        // 多型宣告：宣告父類別，建立子類別
        Order o = new OrderA("o", 20); 
        
        o.showOrder(); // OK, Order 有此方法
        
        // o.showA(); // [錯誤] Order 類別沒有 showA 方法
        
        // [正確] 強制轉型 (Downcasting)
        // 告訴編譯器：「我知道它是 OrderA，請把它當作 OrderA 來用」
        ((OrderA)o).showA(); 
        
        // 多型呼叫 show() -> 執行 OrderA 的 show()
        System.out.println(o.show()); 
    }
}

// [Add3.java] 多型陣列 (Polymorphic Array)
class Day11_PolyArray_Test {
    public static void main(String[] args) {
        // 宣告父類別陣列 (可以放任何 Order 的子孫)
        // 二維陣列不規則宣告
        Order[][] o = new Order[3][];
        o[0] = new Order[3];
        o[1] = new Order[4];

        // 放入不同子類別物件 (Heterogeneous Collection)
        o[0][0] = new OrderA("a1", 10); // A is-an Order
        o[0][1] = new OrderA("a2", 10);
        // 假設有 OrderB, OrderC...
        // o[1][0] = new OrderB("b1", 20); 

        System.out.println("=== 多型陣列遍歷 ===");
        for(int i=0; i<o.length; i++) {
            if(o[i] == null) continue;
            for(int j=0; j<o[i].length; j++) {
                if(o[i][j] != null) {
                    // 自動判斷是 A 還是 B，執行各自的 show (動態繫結)
                    System.out.println(o[i][j].show());
                }
            }
        }
    }
}
```
# Part 5: 抽象與介面 (Day 12 - Day 13)

---

## Day 12: 抽象類別與 Final (Abstract Classes & Final)

### 1. 核心觀念 (Key Concepts)
- **抽象類別 (Abstract Class)**：
    - 使用 `abstract` 修飾的類別。它是「半成品」的藍圖。
    - **限制**：**不能被實體化 (Cannot instantiate)**，即 `new Student()` 是非法的。
    - **用途**：專門用來被繼承 (Extended)，作為子類別的共同模板。
- **抽象方法 (Abstract Method)**：
    - 只有定義 (簽章)，**沒有實作 (Body)**。
    - **強制性**：繼承抽象類別的子類別，**必須實作 (Override)** 所有的抽象方法，除非子類別也是抽象的。
- **Final 關鍵字**：
    - 修飾變數：**常數 (Constant)**，數值一旦給定就不能改。
    - 修飾方法：不能被覆寫 (Override)。
    - 修飾類別：不能被繼承 (Inheritance) (絕育)。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **抽象方法格式**：抽象方法後面是分號 `;`，而不是大括號 `{}`。
- **轉型錯誤**：`School s = new A();` 時，若 `s` 要呼叫 `A` 的獨有方法，必須轉型 `((A)s).method()`。
- **final 賦值**：`final` 變數必須在宣告時或建構子中賦值，且只能賦值一次。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `abstract class Name` | 定義抽象類別 |
| `abstract void method();` | 定義抽象方法 (注意分號) |
| `final double PI = 3.14;` | 定義常數 |
| `final void method()` | 不可覆寫的方法 |
| `final class Name` | 不可繼承的類別 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Student.java, A.java, B.java, C.java, School.java, Ex1.java, Ex2.java)**：

```java
// [Student.java] 抽象類別定義
abstract class Student {
    private String name;
    
    Student(String name) {
        this.name = name;
    }
    
    String show() {
        return "名:" + name;
    }

    // 抽象方法：我只訂規格，內容交給孩子們決定
    // 強迫子類別一定要寫出 set 這個方法
    abstract void set(int o); 
}

// [A.java] 實作抽象類別 (Concrete Class)
class A extends Student {
    private int chi;

    A(String name, int chi) {
        super(name);
        this.chi = chi;
    }

    // 實作父類別的抽象方法
    @Override
    void set(int chi) {
        setChi(chi);
    }
    
    void setChi(int chi) {
        this.chi = chi;
    }

    String show() {
        return super.show() + "\t國文:" + chi;
    }
}

// [B.java] 另一個實作
class B extends Student {
    private int eng;
    B(String name, int eng) {
        super(name);
        this.eng = eng;
    }
    
    @Override
    void set(int eng) {
        setEng(eng);
    }
    
    void setEng(int eng) {
        this.eng = eng;
    }
}

// [Ex2.java] 測試抽象類別與多型
class Day12_Abstract_Test {
    public static void main(String[] args) {
        // Student s = new Student("error"); // [錯誤] 抽象類別不能 new

        // 多型宣告：宣告父類別，建立子類別
        Student a2 = new A("a2", 80); 
        System.out.println(a2.show());

        // 呼叫抽象方法 (實際上會跑 A 的 set)
        a2.set(70); 
        
        // 若要呼叫 A 獨有的 setChi (非繼承來的)，需轉型
        ((A)a2).setChi(90);
    }
}

// [School.java] Final 關鍵字展示
class School {
    double pi = 3.14;
    final double pi2 = 3.14; // 常數 (Instance constant)
    static final double pi4 = 3.14; // 靜態常數 (Class constant, 全域共用)

    // final 方法：子類別不能覆寫此方法
    final void skill() {
        System.out.println("School skill - Cannot Override");
    }
}
```

---

## Day 13: 介面 (Interfaces)

### 1. 核心觀念 (Key Concepts)
- **介面 (Interface)**：
    - 一種完全抽象的結構，像是「規格書 (Contract)」。
    - **特色**：類別可以 **implements (實作)** 多個介面，解決了 Java 單一繼承的限制。
    - **成員預設值**：
        - 變數：預設為 `public static final` (常數)。
        - 方法：預設為 `public abstract` (抽象方法)。
- **多重繼承 (Multiple Inheritance)**：
    - Java 類別只能 `extends` 一個父類別，但可以 `implements` 多個介面。
    - 介面之間可以多重 `extends`。
- **Java 8 新特性**：
    - `default` 方法：介面可以有實作的方法，供子類別直接使用或覆寫。
    - `static` 方法：介面的工具方法。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **介面不能 new**：跟抽象類別一樣，介面不能實體化。
- **實作全部方法**：實作介面的類別 (`implements`) 必須把介面裡所有抽象方法都寫出來，否則自己也要變成 `abstract class`。
- **存取權限**：實作介面方法時，權限必須是 `public` (因為介面預設是 public)。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `interface Name` | 定義介面 |
| `class A implements I1, I2` | 類別實作多個介面 |
| `interface I3 extends I1, I2` | 介面繼承多個介面 |
| `default void method() {}` | (Java 8+) 介面預設方法 |
| `static void method() {}` | (Java 8+) 介面靜態方法 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 School.java, School1~5.java, A.java, B.java, Sa.java, Ex1.java)**：

```java
// [School.java] 介面定義 (規格書)
interface School {
    // 1. 常數 (隱含 public static final)
    String schoolName = "gjun"; 

    // 2. 抽象方法 (隱含 public abstract)
    String bookName(String bookname);
    double bookPrice(double price);

    // 3. Default Method (Java 8+) - 有實作，子類別可直接用
    default void show1() {
        System.out.println("School test-default");
    }

    // 4. Static Method (Java 8+) - 屬於介面本身
    static void show2() {
        System.out.println("School test-static");
    }
}

// [A.java] 實作介面
class A implements School {
    void showA() { System.out.println("A example"); }

    // 必須實作介面的方法，且要是 public
    public double bookPrice(double price) {
        return price;
    }
    public String bookName(String bookname) {
        return bookname;
    }
    // 可以覆寫 default 方法
    public void show1() {
        System.out.println("A override default");
    }
}

// [Sa.java] 繼承類別 + 實作多個介面 (Power of Java)
// 先 extends 類別，再 implements 介面 (順序不可顛倒)
class Sa extends School1 implements School2, School3 {
    Sa(String name) {
        super(name);
    }
    // 必須實作所有介面 (School2, School3, School4, School5...) 規定的方法
    public void show2() {}
    public void show3() {}
    public void show5() {}
}

// [Ex1.java] 測試介面
class Day13_Interface_Test {
    public static void main(String[] args) {
        // 1. 存取介面常數
        System.out.println(School.schoolName);
        
        // 2. 呼叫介面靜態方法
        School.show2();

        // 3. 多型操作：用介面變數操作實作物件
        School s = new A(); 
        System.out.println(s.bookName("Java"));
        s.show1(); // 呼叫 A 覆寫後的 default 方法
        
        // s.showA(); // [錯誤] 介面看不到實作類別的獨有方法
        ((A)s).showA(); // [正確] 強制轉型
        
        // 4. 介面陣列 (多型陣列)
        School[] s2 = new School[2];
        s2[0] = new A();
        // s2[1] = new B(); 
        
        for(School o : s2) {
            if(o != null) System.out.println(o.bookName("Book"));
        }
    }
}

// 輔助介面與類別 (模擬多重繼承結構)
class School1 { School1(String s){} }
interface School2 { void show2(); }
interface School4 { void show2(); } // 若方法簽章相同，實作一次即可
interface School5 { void show5(); }
// 介面可以繼承多個介面
interface School3 extends School4, School5 { void show3(); }
```

# Part 6: 例外處理與斷言 (Day 14 - Day 15)

---

## Day 14: 例外處理基礎 (Exception Handling Basics)

### 1. 核心觀念 (Key Concepts)
- **例外 (Exception)**：
    - 程式執行期間發生的錯誤 (Runtime Error)，會導致程式非正常中斷 (Crash)。
    - Java 使用物件來代表錯誤，如 `ArithmeticException` (數學錯誤)、`ArrayIndexOutOfBoundsException` (陣列越界)。
- **例外處理機制 (Try-Catch)**：
    - **try**：監控區塊。將可能發生錯誤的程式碼放在這裡。
    - **catch**：捕捉區塊。當 try 中發生特定例外時，執行這裡的補救措施或顯示訊息。
    - **finally** (補充觀念)：無論是否發生例外，都一定會執行的區塊 (通常用於關閉資源)。
- **例外階層 (Hierarchy)**：
    - `Throwable` (所有錯誤的祖先)
        - `Error`：嚴重系統錯誤 (如 OutOfMemory)，通常無法程式處理。
        - `Exception`：程式可處理的例外。
            - `RuntimeException` (Unchecked)：編譯器不強迫檢查 (如 NullPointer)。
            - 其他 (Checked)：編譯器強迫檢查 (如 IOException)。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **Catch 順序**：子類別例外 (如 `ArithmeticException`) 必須寫在父類別例外 (如 `Exception`) 之前，否則會編譯錯誤 (Unreachable code)。
- **變數範疇**：在 `try` 區塊內宣告的變數，在 `catch` 區塊是看不到的。變數應在 try 之前宣告。
- **忽略例外**：`catch` 裡面什麼都不寫 (空區塊)，這會讓錯誤「被吃掉」，導致除錯極其困難。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `try { ... }` | 監控區塊 |
| `catch(Type e) { ... }` | 捕捉並處理例外 |
| `catch(T1 | T2 e)` | (Java 7+) 多重捕捉 (Multi-Catch) |
| `e.printStackTrace()` | 印出錯誤堆疊追蹤 (Debug 用) |
| `e.getMessage()` | 取得錯誤簡短訊息 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Ex1.java)**：

```java
import java.util.Scanner;
import java.util.InputMismatchException;

class Day14_Exception_Demo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[] x = new int[3]; // 索引範圍 0~2
        
        System.out.println("請輸入索引 (0-2):");

        try {
            // [危險區域] 可能發生多種例外
            int n = sc.nextInt(); // 1. 輸入非數字 -> InputMismatchException
            x[n] = 10;            // 2. 輸入 3 -> ArrayIndexOutOfBoundsException

            System.out.println("請輸入分母:");
            int m = sc.nextInt();
            // 3. 輸入 0 -> ArithmeticException
            System.out.println("x["+n+"] / "+m+" = " + (x[n]/m)); 
            
            // 迴圈示範：若上面發生例外，這裡會被跳過
            for(int i=1; i<=3; i++) {
                System.out.println("Process " + i);
            }
        }
        
        // [捕捉特定例外]
        catch(ArrayIndexOutOfBoundsException e) {
            System.out.println("錯誤：索引需介於 0~2");
            e.printStackTrace(); // 印出紅字錯誤詳情
        }
        
        // [Java 7 Multi-Catch] 同時捕捉多種例外 (適合處理邏輯相同時)
        catch(InputMismatchException | ArithmeticException e) {
            System.out.println("錯誤：輸入格式錯誤 或 分母不可為 0");
        }
        
        // [捕捉剩餘所有例外] (父類別 Exception 要放在最後)
        catch(Exception e) {
            System.out.println("發生未預期的錯誤");
        }
        
        System.out.println("程式正常結束");
    }
}
```

---

## Day 15: 進階例外與斷言 (Advanced Exceptions & Assertions)

### 1. 核心觀念 (Key Concepts)
- **Throws (消極處理/宣告拋出)**：
    - 在方法宣告處標示 `throws Exception`。
    - 意義：「我這個方法可能會出錯，但我不想處理，請呼叫我的人 (Caller) 去處理」。
    - 對於 **Checked Exception** (如 `IOException`, `FileNotFoundException`)，Java 強制要求必須處理 (try-catch) 或宣告拋出 (throws)。
- **Throw (主動拋出)**：
    - 在程式邏輯中，主動產生一個例外物件並丟出。
    - 語法：`throw new Exception("錯誤訊息");`
    - 用途：當資料不符合商業邏輯 (如年齡為負數) 時，中斷流程。
- **自訂例外 (Custom Exception)**：
    - 繼承 `Exception` (Checked) 或 `RuntimeException` (Unchecked) 類別。
    - 建立專屬於專案的錯誤型別 (如 `Check` 類別)，讓錯誤訊息更明確。
- **斷言 (Assertion)**：
    - 用於開發階段的測試工具。假設某條件為真，若為假則程式中止 (拋出 `AssertionError`)。
    - 預設是關閉的，執行時需加 VM 參數 `-ea` (Enable Assertions) 才會生效。

### 2. 新手常弄錯該注意的地方 (Beginner Mistakes)
- **Throw vs Throws**：
    - `throw`：動作，在方法**內部**丟出例外物件。
    - `throws`：宣告，在方法**簽章**旁宣告可能丟出的例外類型。
- **建構子例外**：若建構子宣告了 `throws Exception`，那麼在 `new` 這個物件時，就必須 try-catch 或繼續 throws。
- **Assert 誤用**：斷言不應用於檢查使用者輸入或公開方法的參數 (因為生產環境通常會關閉 -ea)，只應用於內部邏輯檢核。

### 3. 本日新增語法 (New Syntax)
| 語法 | 說明 |
| :--- | :--- |
| `void m() throws Ex1, Ex2` | 方法宣告拋出例外 |
| `throw new Exception("msg")` | 程式碼中主動拋出例外 |
| `class MyEx extends Exception` | 定義自訂例外類別 |
| `assert condition : "msg";` | 斷言檢查 (若 false 則崩潰) |
| `java -ea ClassName` | 執行時開啟斷言功能 |

### 4. 實戰代碼解析 (Code Analysis)

**整合範例 (包含 Check.java, Order.java, Ex1.java, Ex2.java, Ex3.java, Add1.java)**：

```java
import java.io.File;
import java.io.IOException;
import java.util.Scanner;

// [Check.java] 自訂例外類別
// 繼承 Exception 代表它是 Checked Exception，必須被處理
class Check extends Exception {
    Check(String errMsg) {
        // 呼叫父類別建構子存入訊息
        super(errMsg); 
        System.out.println("自訂檢查錯誤: " + errMsg);
    }
}

// [Order.java] 在邏輯中使用 throw 與 throws
class Order {
    private String name;
    private int ram;
    private int lcd;

    // 建構子：宣告可能拋出 Check 例外
    Order(String name, int ram, int lcd) throws Check {
        if(ram >= 0 && lcd >= 0) {
            this.name = name;
            this.ram = ram;
            this.lcd = lcd;
        } else {
            // [關鍵] 邏輯錯誤時，主動丟出例外物件，阻止物件建立
            throw new Check("新增 ram 與 lcd 需 >= 0");
        }
    }
    
    // Setter 也要檢查
    void setLcd(int lcd) throws Check {
        if(lcd >= 0) this.lcd = lcd;
        else throw new Check("修改 lcd 需 >= 0");
    }
    
    void show() { System.out.println(name + "\t" + ram + "\t" + lcd); }
}

// [Ex2.java] 測試 Checked Exception (IOException)
class Day15_Checked_Demo {
    // 選擇用 throws 拋給 JVM 處理 (偷懶寫法)，不想寫 try-catch
    public static void main(String[] args) throws IOException {
        File f = new File("c:/abc.txt");
        // createNewFile 是 Checked Exception，編譯器強迫處理
        f.createNewFile(); 
    }
}

// [Ex3.java] 測試自訂例外與斷言
class Day15_Throw_Assert_Demo {
    // main 也宣告 throws Check，因為懶得 try-catch Order 的建構子
    public static void main(String[] args) throws Check {
        Order[] o = new Order[3];
        
        // 這裡若參數給負數，會拋出 Check 例外並中斷程式
        o[0] = new Order("a1", 4, 5); 
        o[1] = new Order("d2", 7, 7);

        Scanner sc = new Scanner(System.in);
        System.out.println("輸入要修改的Lcd數量:");
        int lcd = sc.nextInt();

        // [斷言 Assertion]
        // 執行時需打: java -ea Day15_Throw_Assert_Demo
        // 若 lcd < 0，程式會拋出 AssertionError 並顯示訊息
        assert lcd >= 0 : "lcd 需要 >= 0 (斷言失敗)"; 

        o[1].setLcd(lcd); // 若斷言通過才會執行這行
        
        for(int i=0; i<o.length; i++) {
            if(o[i] != null) o[i].show();
        }
    }
}
```