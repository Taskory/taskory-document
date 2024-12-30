## ENG

**1. Overview**

This document details the system architecture design of a schedule and to-do list management application. The system is designed to efficiently manage multiple calendars and to-do lists, based on a multi-layered architecture to meet various user requirements.

**2. Architecture Overview**

The system follows a multi-layered architecture based on the client-server model. The main components are as follows:

1. **Frontend (Client)**

2. **Backend (Server)**

3. **Database**

4. **Third-Party API**

5. **Notification Service**

Each component is designed independently and communicates via REST APIs.

**3. System Components**

**3.1 Frontend**

- **Tech Stack**: React (TypeScript), HTML, TailwindCSS

- Features:

  - Provides the user interface

  - Visual management of calendars and to-do lists

  - User authentication and authorization

  - Communication with the backend via REST API

  - Push notifications and real-time updates

**3.2 Backend**

- **Tech Stack**: Java (Spring Boot)

- Features:

  - User authentication and authorization

  - Management of calendars and to-do lists

  - Communication with the database

  - Integration with third-party APIs (e.g., Google Calendar)

  - Communication with the notification service

  - Provides REST APIs

**3.3 Database**

- **Tech Stack**: MariaDB

- Features:

  - Storage and management of user data

  - Storage of calendar and to-do list data

  - Management of routines, tags, and hashtags data

  - Indexing and query optimization

**3.4 Third-Party API**

- **Components**: Google Calendar API, Facebook API, etc.

- Features:

  - Social calendar integration

  - Authentication and data synchronization with external services

**3.5 Notification Service**

- **Tech Stack**: Firebase Cloud Messaging (FCM)

- Features:

  - Sending push notifications

  - Sending email notifications

  - Management of notification settings

**4. Detailed Architecture**

**4.1 Frontend**

The frontend directly interacts with users and is developed as a Single Page Application (SPA) using React and TypeScript.

- Structure:

  - **Components**: Basic units forming the UI

  - **Pages**: Pages corresponding to specific routes

  - **Services**: API calls and data management

  - **State Management**: Global state management using Redux or Context API

  - **Routing**: Client-side routing using React Router

  - **Styles**: Styling using TailwindCSS, DaisyUI

**4.2 Backend**

The backend is developed using Spring Boot and provides RESTful APIs. It is designed with a modular structure for each functionality.

- Structure:

  - **Controller**: Handles HTTP requests and calls appropriate services

  - **Service**: Processes business logic

  - **Repository**: Interacts with the database

  - **Entity**: Classes mapping to database tables

  - **DTO**: Data Transfer Objects

  - **Security**: Authentication and authorization using Spring Security

**4.3 Database**

The database uses MariaDB and is designed based on a relational data model.

- Table Structure:

  - **User**: User information (ID, name, email, password hash, social account info, etc.)

  - **Event**: Event information (ID, calendar ID, title, description, start date, end date, recurrence settings, etc.)

  - **Task Group**: To-do list information (ID, user ID, name, description, etc.)

  - **Task**: Individual to-do information (ID, list ID, title, description, due date, priority, completion status, etc.)
  - **Check**: Detailed checklist for tasks (ID, title, check status, parent task)

  - **Routine**: Routine information (ID, user ID, name, description, frequency, notification settings, etc.)

  - **Tag**: Tag information (ID, user ID, name, etc.)

  - **Hashtag**: Hashtag information (ID, user ID, name, etc.)

  - **Notification**: Notification information (ID, user ID, type, message, send time, etc.)

**4.4 Third-Party API Integration**

Third-party API integration handles authentication using OAuth2 and synchronizes data with services like Google Calendar API.

- Structure:

  - **OAuth2 Client**: Handles authentication (manages access tokens and refresh tokens)

  - **API Client**: Calls third-party APIs

  - **Sync Service**: Data synchronization logic (sync cycles, reflecting changes, etc.)

**4.5 Notification Service**

The notification service uses FCM to send push notifications, and emails are sent via an SMTP server.

- Structure:

  - **Notification Service**: Handles notification logic (push and email)

  - **Push Notification**: Push notifications via FCM

  - **Email Notification**: Email notifications via SMTP (to be implemented)

  - **Notification Settings**: Manages user notification settings

**5. System Communication**

Each component communicates via REST APIs, with the main communication flows as follows:

1. Frontend <-> Backend:

- User authentication (login, signup, password reset, etc.)

- CRUD operations for calendars and to-do lists

- Notification settings and reception

2.	Backend <-> Database:

- Data storage and retrieval (users, events, schedules, to-do lists, etc.)

3. Backend <-> Third-Party API:

- Social calendar synchronization (OAuth2 authentication, API calls, etc.)

4. Backend <-> Notification Service:

- Notification sending requests (push and email)

## KOR

#### 1. 개요

이 문서는 일정 및 할 일 관리 애플리케이션의 시스템 구조 설계를 기술합니다. 본 시스템은 여러 캘린더와 할 일 목록을 효율적으로 관리하기 위해 설계되었으며, 다양한 사용자 요구사항을 충족하기 위한 다층 아키텍처를 기반으로 합니다.

#### 2. 아키텍처 개요

본 시스템은 클라이언트-서버 모델을 따르는 다층 아키텍처로 구성됩니다. 주요 구성 요소는 다음과 같습니다:

1. **프론트엔드 (클라이언트)**
2. **백엔드 (서버)**
3. **데이터베이스**
4. **서드 파티 API**
5. **알림 서비스**

각 구성 요소는 독립적으로 설계되어 있으며, REST API를 통해 통신합니다.

#### 3. 시스템 구성 요소

##### 3.1 프론트엔드

- **기술 스택**: React (TypeScript), HTML, TailwindCSS

- 기능

  :

  - 사용자 인터페이스 제공
  - 캘린더 및 할 일 목록의 시각적 관리
  - 사용자 인증 및 권한 관리
  - REST API를 통한 백엔드와의 통신
  - 푸시 알림 및 실시간 업데이트

##### 3.2 백엔드

- **기술 스택**: Java (Spring Boot)

- 기능

  :

  - 사용자 인증 및 권한 관리
  - 캘린더 및 할 일 목록 관리
  - 데이터베이스와의 통신
  - 서드 파티 API 연동 (구글 캘린더 등)
  - 알림 서비스와의 통신
  - REST API 제공

##### 3.3 데이터베이스

- **기술 스택**: MariaDB

- 기능

  :

  - 사용자 데이터 저장 및 관리
  - 캘린더 및 할 일 목록 데이터 저장
  - 루틴, 태그, 해시태그 데이터 관리
  - 인덱싱 및 쿼리 최적화

##### 3.4 서드 파티 API

- **구성 요소**: Google Calendar API, Facebook API 등

- 기능

  :

  - 소셜 캘린더 연동
  - 외부 서비스와의 인증 및 데이터 동기화

##### 3.5 알림 서비스

- **기술 스택**: Firebase Cloud Messaging (FCM)

- 기능

  :

  - 푸시 알림 전송
  - 이메일 알림 전송
  - 알림 설정 관리

#### 4. 상세 아키텍처

##### 4.1 프론트엔드

프론트엔드는 사용자와 직접 상호작용하는 부분으로, React와 TypeScript를 사용하여 SPA (Single Page Application) 형태로 개발됩니다.

- 구조

  :

  - **Components**: UI를 구성하는 기본 단위
  - **Pages**: 특정 라우트에 대응하는 페이지
  - **Services**: API 호출 및 데이터 관리
  - **State Management**: Redux 또는 Context API를 이용한 전역 상태 관리
  - **Routing**: React Router를 이용한 클라이언트 사이드 라우팅
  - **Styles**: TailwindCSS, DaisyUI를 이용한 스타일링

##### 4.2 백엔드

백엔드는 Spring Boot를 사용하여 개발되며, RESTful API를 제공합니다. 각 기능별로 모듈화된 구조로 설계됩니다.

- 구조

  :

  - **Controller**: HTTP 요청을 처리하고 적절한 서비스 호출
  - **Service**: 비즈니스 로직 처리
  - **Repository**: 데이터베이스와의 상호작용
  - **Entity**: 데이터베이스 테이블과 매핑되는 클래스
  - **DTO**: 데이터 전송 객체
  - **Security**: Spring Security를 이용한 인증 및 권한 관리

##### 4.3 데이터베이스

데이터베이스는 MariaDB를 사용하여 관계형 데이터 모델을 기반으로 설계됩니다.

- 테이블 구조

  :

  - **User**: 사용자 정보 (ID, 이름, 이메일, 비밀번호 해시, 소셜 계정 정보 등)
  - **Event**: 일정 정보 (ID, 캘린더 ID, 제목, 설명, 시작일, 종료일, 반복 설정 등)
  - **Task Group**: 할 일 목록 정보 (ID, 사용자 ID, 이름, 설명 등)
  - **Task**: 개별 할 일 정보 (ID, 목록 ID, 제목, 설명, 마감 기한, 우선순위, 완료 여부 등)
  - **Check**: 할 일에 대한 세부 체크리스트(ID, 제목, 체크 여부, 부모 할 일)
  - **Routine**: 루틴 정보 (ID, 사용자 ID, 이름, 설명, 주기, 알림 설정 등)
  - **Tag**: 태그 정보 (ID, 사용자 ID, 이름 등)
  - **Hashtag**: 해시태그 정보 (ID, 사용자 ID, 이름 등)
  - **Notification**: 알림 정보 (ID, 사용자 ID, 종류, 메시지, 전송 시간 등)

##### 4.4 서드 파티 API 연동

서드 파티 API 연동은 OAuth2를 사용하여 인증을 처리하며, Google Calendar API와 같은 서비스를 통해 데이터 동기화를 수행합니다.

- 구조

  :

  - **OAuth2 Client**: 인증 처리 (Access Token 및 Refresh Token 관리)
  - **API Client**: 서드 파티 API 호출
  - **Sync Service**: 데이터 동기화 로직 (동기화 주기, 변경사항 반영 등)

##### 4.5 알림 서비스

알림 서비스는 FCM을 사용하여 푸시 알림을 전송하며, 이메일 알림은 SMTP 서버를 통해 전송됩니다.

- 구조

  :

  - **Notification Service**: 알림 전송 로직 (푸시 및 이메일)
  - **Push Notification**: FCM을 통한 푸시 알림
  - **Email Notification**: SMTP를 통한 이메일 알림
    - 추후 적용
  - **Notification Settings**: 사용자의 알림 설정 관리

#### 5. 시스템 통신

각 구성 요소는 REST API를 통해 통신하며, 주요 통신 흐름은 다음과 같습니다:

1. 프론트엔드 <-> 백엔드

   :

   - 사용자 인증 (로그인, 회원가입, 비밀번호 재설정 등)
   - 캘린더 및 할 일 목록 CRUD 작업
   - 알림 설정 및 수신

2. 백엔드 <-> 데이터베이스

   :

   - 데이터 저장 및 조회 (사용자, 이벤트, 일정, 할 일 목록 등)

3. 백엔드 <-> 서드 파티 API

   :

   - 소셜 캘린더 동기화 (OAuth2 인증, API 호출 등)

4. 백엔드 <-> 알림 서비스

   :

   - 알림 전송 요청 (푸시 및 이메일)
