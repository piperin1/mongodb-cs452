# MyPomo — A Customizable Pomodoro Timer

## Summary
MyPomo hinges on the **Pomodoro Technique**, which typically breaks work into 25-minute intervals with 5-minute breaks. In the past, I've used pomodoro timers to better manage my workflow and motivation—but I wanted more flexibility and customization options. MyPomo solves this problem by allowing users to customize their own pomodoro timer, including interval and break times, themes, and music. As a web application, MyPomo can be accessed by anyone with an internet connection. 

Supported by Flask, Neon, and PostgreSQL, MyPomo will remember user preferences through a simple login system and session management, allowing individuals to maintain their custom timers across devices and locations. MyPomo aims to benefit individuals who need additional support in their workflow management, task motivation, and more.

## ERD
```mermaid
erDiagram
  USERS ||--|| PREFERENCES : has
  USERS ||--o{ POMODORO_SESSIONS : logs
  THEMES ||--o{ PREFERENCES : "chosen in"
  FONTS ||--o{ PREFERENCES : "chosen in"
  SOUNDS ||--o{ PREFERENCES : "start/end sound"
 
  USERS {
    int id PK
    varchar username UK
    varchar password_hash
    timestamp created_at
  }
  PREFERENCES {
    int user_id PK,FK
    int theme_id FK
    int font_id FK
    int start_sound_id FK
    int end_sound_id FK
    int work_min
    int short_break_min
    int long_break_min
    varchar music_url
  }
  THEMES {
    int id PK
    varchar name
    varchar bg_color
    varchar text_color
    varchar accent_color
  }
  FONTS {
    int id PK
    varchar name
    varchar css_family
  }
  SOUNDS {
    int id PK
    varchar name
    varchar file_path
  }
  POMODORO_SESSIONS {
    int id PK
    int user_id FK
    varchar type
    timestamp started_at
    timestamp ended_at
    boolean completed
  }
```
## System Design
![MyPomo system layout](./mypomo_layout.png)
## Daily Goals
- Spend at least ~1hr developing MyPomo application
- Develop with usability in mind
- Approach MyPomo tasks strategically rather than spontaneously