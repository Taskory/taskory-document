## ENG

**Event**

- **id**: Unique identifier for the event
- **parent_user**: Identifier for the user who created the event
- **title**: Name of the event
- **tag**: Tag or category for the event - nullable
- **hashtag**: Hashtag for the event - nullable
- **description**: Additional description or notes about the event - nullable
- **start_date_time**: Start date and time of the event
- **end_date_time**: End date and time of the event
- **location**: Location where the event takes place - nullable
- **created_at**: Creation timestamp
- **updated_at**: Last update timestamp

**Flow**

- **id**: Unique identifier for the task group
- **parent_user**: Identifier for the user who created the task group
- **title**: Name of the task group
- **hashtag**: Hashtag for the task group - nullable
- **description**: Additional description or notes about the task group - nullable
- **created_at**: Creation timestamp
- **updated_at**: Last update timestamp

**Task**

- **id**: Unique identifier for the task
- **parent_user**: Identifier for the user who created the task
- **title**: Name of the task
- **parent_flow**: Identifier for the task group related to the task - nullable
- **parent_event**: Identifier for the event related to the task - nullable
- **tag**: Tag or category for the task
- **hashtag**: Hashtag for the task - nullable
- **description**: Additional description or notes about the task - nullable
- **status**: Status of the task (e.g., Todo, InProgress, Done)
- **created_at**: Creation timestamp
- **updated_at**: Last update timestamp

**TaskItem(checklist)**

- **id**: Unique identifier for the task item
- **parent_user**: Identifier for the user who created the task item
- **title**: Name of the task item
- **completed**: Boolean indicating whether the task item is completed

**Routine**

- **id**: Unique identifier for the routine

- **parent_user**: Identifier for the user who created the routine

- **title**: Name of the routine

- **description**: Additional description or notes about the routine - nullable

- **days**: Days or frequency when the routine occurs

**Routine History**

- **id**: Unique identifier for the routine history record

- **parent_user**: Identifier for the user

- **parent_routine**: Identifier for the related routine

- **completed_at**: Timestamp when the routine was executed

**Tag**

- **id**: Unique identifier for the tag
- **parent_user**: Identifier for the user who created the tag
- **name**: Name of the tag
- **color**: Color of the tag

**Hashtag**

- **id**: Unique identifier for the hashtag**
- parent_user**: Identifier for the user who created the hashtag**
- **name**: Name of the hashtag

**User**

- **id**: Unique identifier for the user
- **username**: User’s ID or email
- **social_account**: Information about the user’s linked social accounts
- **password**: User’s password
- zoneId: User's timezone

**SocialAccount**

- **id**: Unique identifier for the social account link**
- subid**: Unique ID provided by the social provider**
- user_id**: Unique identifier for the user**
- username**: Email or ID of the social account**
- name**: Name of the user in the social account**
- **provider**: Social provider (e.g., Google, Facebook)

## KOR

**Event  **:

- id: 일정의 고유 식별자
- parent_user: 일정을 생성한 사용자의 식별자
- title: 일정의 이름
- tag: 일정에 대한 태그 또는 카테고리 - nullable
- hashtag: 일정의 해시태그 - nullable
- description: 일정에 대한 추가 설명 또는 메모 - nullable
- start_date_time: 일정 시작 일시
- end_date_time: 일정 종료 일시
- location: 일정이 진행되는 장소 - nullable
- child_task_group: 해당 일정과 연관된 작업 집합의 식별자 - nullable
- created_at: 생성 시간
- updated_at: 수정 시간

**Flow  **:

- id: 작업 집합의 고유 식별자
- parent_user: 작업 집합을 생성한 사용자의 식별자
- title: 작업 집합의 이름
- hashtag: 작업 집합의 해시태그 - nullable
- description: 작업 집합에 대한 추가 설명 또는 메모 - nullable
- child_tasks: 해당 작업 집합의 작업들 - nullable
- created_at: 생성 시간
- updated_at: 수정 시간

**Task  **:

- id: 작업의 고유 식별자
- parent_user: 작업을 생성한 사용자의 식별자
- title: 작업의 이름
- parent_flow: 해당 작업과 연관된 작업 집합의 식별자 - nullable
- parent_event: 해당 작업과 연관된 일정의 식별자 - nullable
- tag: 작업에 대한 태그 또는 카테고리 - nullable
- hashtag: 작업의 해시태그 - nullable
- description: 작업에 대한 추가 설명 또는 메모 - nullable
- status: 작업의 상태 (Todo, InProgress, Done 등)
- due_date_time: 작업의 마감 일시 - nullable
- created_at: 생성 시간
- updated_at: 수정 시간

**TaskItem(checklist)**

1. id: 체크의 고유 식별자
2. parent_user: 체크를 생성한 사용자의 식별자
3. title: 체크의 이름
4. parent_task: 해당 체크와 연관된 작업의 식별자
5. completed - boolean: 체크 여부

**Routine  **:

- id: 루틴의 고유 식별자
- parent_user: 루틴을 생성한 사용자의 식별자
- title: 루틴의 이름
- description: 루틴에 대한 추가 설명 또는 메모 - nullable
- days: 루틴이 발생하는 요일 또는 주기

Routine History
- id: 루틴 기록의 고유 식별자
- parent_user: 사용자의 식별자
- parent_routine: 루틴의 고유 식별자
- completed_at: 실행한 시간

**Tag  **:

- id: 태그의 고유 식별자
- parent_user: 태그를 생성한 사용자의 식별자
- name: 태그의 이름
- color: 태그의 색상

**Hashtag  **:

- id: 해시태그의 고유 식별자
- parent_user: 해시태그를 생성한 사용자의 식별자
- name: 해시태그의 이름

User  

- id: 사용자의 고유 식별자

- username: 사용자의 id or email

- social_account: 사용자가 연동한 소셜 계정 정보

- password

SocialAccount
- id: 소셜 연동 계정의 고유 식별자
- subid: 소셜 연동에서 제공하는 고유 id
- user_id: 사용자의 고유 id
- username: 소셜 계정의 이메일 및 ID
- name: 소셜 계정에서의 사용자의 이름
- provider: 소셜 제공자(ex. google, facebook)
