# TogetherShop Backend

TogetherShop은 공동구매 플랫폼을 위한 Spring Boot 기반 RESTful API 서버입니다. 사용자들이 함께 구매하여 할인 혜택을 받을 수 있는 서비스로, 고객과 사업자를 연결하여 효율적인 공동구매 경험을 제공합니다.[1]

## 프로젝트 개요

이 프로젝트는 Java 17과 Spring Boot 3.5.5를 기반으로 하며, JWT 인증, WebSocket 실시간 통신, Redis 캐싱 등 현대적인 백엔드 기술 스택을 활용합니다. 레이어드 아키텍처를 따르며 도메인 주도 설계(DDD) 원칙을 적용하고 있습니다.[1]

## 기술 스택

### 핵심 프레임워크
- **Spring Boot** 3.5.5
- **Spring Data JPA**: 데이터 영속성 관리
- **Spring Security**: 인증 및 인가 처리
- **Spring WebSocket & STOMP**: 실시간 채팅 통신[1]

### 데이터베이스 및 캐싱
- **MySQL**: 주요 관계형 데이터베이스
- **Redis**: 세션 관리 및 캐싱[1]

### 보안 및 인증
- **JJWT** 0.11.5: JWT 토큰 기반 인증
- **Spring Security**: 권한 관리 및 보안 필터[1]

### 외부 서비스 통합
- **Firebase Admin SDK** 9.2.0: FCM 푸시 알림 전송
- **ZXing** 3.5.1: QR 코드 생성 및 스캔[1]

### 빌드 도구
- **Gradle**: 의존성 관리 및 빌드 자동화[1]

## 아키텍처

프로젝트는 다음과 같은 레이어드 구조로 구성됩니다:[1]

- **Controller Layer**: REST API 엔드포인트 정의
- **Service Layer**: 비즈니스 로직 구현
- **Repository Layer**: 데이터 액세스 계층
- **Domain Layer**: 엔티티 및 도메인 모델
- **DTO Layer**: 데이터 전송 객체
- **Security Layer**: 인증 및 인가 설정
- **Config Layer**: 애플리케이션 설정
- **Exception Layer**: 예외 처리 및 에러 핸들링
- **Util Layer**: 공통 유틸리티 클래스


## 주요 기능

### 1. 이중 사용자 시스템
고객(Customer)과 사업자(Business) 각각에 대한 독립적인 인증 및 권한 관리 시스템을 제공합니다.[1]

### 2. JWT 기반 인증
Access Token과 Refresh Token을 활용한 안전한 토큰 기반 인증 시스템을 구현했습니다.[1]

### 3. 쿠폰 시스템
템플릿 기반 쿠폰 생성, QR 코드를 통한 쿠폰 사용, 사용 내역 추적 기능을 제공합니다.[1]

### 4. 공동구매 프로젝트
사업자가 공동구매를 생성하고, 고객이 참여하여 할인 혜택을 받을 수 있는 시스템입니다.[1]

### 5. 실시간 채팅
WebSocket과 STOMP 프로토콜을 사용한 실시간 채팅 기능으로 참여자 간 소통을 지원합니다.[1]

### 6. 푸시 알림
Firebase Cloud Messaging을 통한 실시간 푸시 알림으로 공동구매 상태 변경, 쿠폰 발급 등의 이벤트를 알립니다.[1]

### 7. QR 코드 기반 쿠폰 사용
ZXing 라이브러리를 활용하여 QR 코드 생성 및 스캔을 통한 쿠폰 사용 프로세스를 구현했습니다.[1]

### 8. 제휴 관리
사업자와 플랫폼 간 제휴 신청, 승인, 성과 리포트 관리 기능을 제공합니다.[1]

## 설치 및 실행

### 사전 요구사항
- Java 17 이상
- MySQL
- Redis
- Gradle[1]


## 프로젝트 구조

```
src/main/java/com/togethershop/backend/
├── config/           # 애플리케이션 설정
├── controller/       # REST API 엔드포인트
├── service/          # 비즈니스 로직
├── repository/       # 데이터 액세스 계층
├── domain/           # 엔티티 모델
├── dto/              # 데이터 전송 객체
├── security/         # 보안 관련 설정
├── exception/        # 예외 처리
└── util/             # 유틸리티 클래스
```

[1](https://github.com/kirikaka/TogetherShop-Back-end)
