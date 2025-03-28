# 📅 캘린더 앱
### **일정 관리, 푸시 알람, 지출 관리를 통합한 안드로이드 애플리케이션**

> 일정 관리와 개인 지출 기록을 효율적으로 통합하고, 중요한 일정을 놓치지 않도록 푸시 알림 기능을 제공하는 Android 기반 캘린더 앱입니다.

---

<img src="https://github.com/user-attachments/assets/195640e9-f6fd-4083-9f04-b3ce9f27145f" width="284" height="334"/>

---

## 🗂 목차
- [1. 개요](#1-개요)
- [2. 주요 기능](#2-주요-기능)
- [3. 코드 구성](#3-코드-구성)
- [4. 실행 화면](#4-실행-화면)
- [5. 실행 방법](#5-실행-방법)
- [6. 기술 스택](#6-기술-스택)

---

## 1. 📌 개요

- 날짜 선택 기반 일정 등록 및 수정
- 일정에 따라 알림 자동 발생
- 당일/전체 지출 내역 관리
- Room DB로 데이터 영속성 유지

---

## 2. ⚙️ 주요 기능

| 기능          | 설명 |
|---------------|------|
| 일정 등록     | 날짜를 클릭하여 일정 입력 가능 |
| 일정 수정     | 기존 일정을 수정 및 삭제 |
| 푸시 알림     | 설정된 일정 시간에 자동 알림 발생 |
| 지출 관리     | 날짜별 지출 입력 및 확인 가능 |
| 로컬 저장소   | Room DB를 활용한 일정/지출 저장 |

---

## 3. 🛠 기술 스택

<img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white"/> 
<img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white"/> 
<img src="https://img.shields.io/badge/Room-6DB33F?style=for-the-badge&logo=sqlite&logoColor=white"/> 
<img src="https://img.shields.io/badge/Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white"/> 
<img src="https://img.shields.io/badge/XML-FF6600?style=for-the-badge&logo=w3c&logoColor=white"/> 

- **Java**: 안드로이드 네이티브 애플리케이션 개발 언어
- **Android SDK**: UI/UX 구성 및 앱의 핵심 기능 구현
- **Room (SQLite 기반)**: 일정 및 지출 정보를 저장하는 로컬 DB 시스템
- **AlarmManager + BroadcastReceiver**: 정해진 시간에 푸시 알림을 보내는 시스템 구성
- **Gradle**: 종속성 관리 및 빌드 자동화 도구
- **XML Layout**: 화면 레이아웃 및 UI 구성 정의

---

## 4. 🧠 코드 구성

```java
// addschedule.java
Schedule schedule = new Schedule(title, date, time);
database.scheduleDao().insert(schedule);
// AlarmReceiver.java
alarmManager.setExact(
  AlarmManager.RTC_WAKEUP, triggerTime, pendingIntent);
// outmoney.java
Expense expense = new Expense(amount, category, date);
database.expenseDao().insert(expense);
```
---
## 5. 🖼 실행 화면

### 📅 메인 캘린더 화면  
사용자가 날짜를 클릭해 일정을 추가하거나 확인할 수 있는 기본 화면입니다.

<img src="https://github.com/user-attachments/assets/195640e9-f6fd-4083-9f04-b3ce9f27145f" width="284" height="334"/>

---

### ➕ 일정 등록 화면  
선택한 날짜에 대한 제목과 시간 등을 입력해 새로운 일정을 등록할 수 있습니다.

<img src="https://github.com/user-attachments/assets/e9fff370-44aa-4321-95c3-78268b3a79c0" width="291" height="334"/>

---

### ⏰ 푸시 알림 화면  
등록된 일정 시간이 되면 자동으로 푸시 알림이 표시되어 사용자가 일정을 놓치지 않도록 합니다.

<img src="https://github.com/user-attachments/assets/72aaeb7a-a945-45d0-b8fa-2ea89f0efc97" width="238" height="391"/>

---

### 💸 지출 관리 화면  
해당 날짜의 지출 내역을 입력하고 저장할 수 있으며, 일별로 합계도 확인할 수 있습니다.

<img src="https://github.com/user-attachments/assets/1c469a81-6335-4cff-9ed3-f420f902b092" width="284" height="368"/>

---

## 6. ▶ 실행 방법

이 프로젝트는 Android Studio에서 바로 실행할 수 있는 구조입니다.

### ✅ 실행 절차

1. **프로젝트 클론**
```bash
git clone https://github.com/hancruyff/Calendar-app.git
```

2. **Android Studio로 프로젝트 열기**

Android Studio 실행 후 “Open” 또는 “Open an Existing Project” 클릭

Calendar-app 폴더 선택

프로젝트 구조상 build.gradle 파일이 있는 루트 디렉토리를 기준으로 열어야 합니다

3. **Gradle Sync 진행**

프로젝트가 열리면 상단에서 Gradle sync가 자동으로 진행됩니다

문제가 있을 경우 File > Sync Project with Gradle Files 메뉴를 클릭하여 수동으로 동기화하세요

4. **에뮬레이터 또는 실제 디바이스 연결**

Android Studio 상단 툴바에서 AVD(가상 디바이스)를 설정하거나,

USB 디버깅이 활성화된 안드로이드 스마트폰을 연결합니다

5. **앱 실행**

MainActivity.java 또는 AddSchedule.java를 열고

▶ 버튼 클릭 또는 Shift + F10 키를 눌러 앱을 빌드 및 실행합니다

앱 확인

캘린더 화면이 기본으로 뜨며,

날짜 클릭 → 일정 추가 → 저장 → 푸시 알림 발생 흐름을 따라 테스트할 수 있습니다
