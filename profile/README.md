# 🛒 POP-CON - 온라인 편의점 쇼핑몰

> 편하게, 빠르게, 익숙하게. 대형 편의점을 집 앞까지 옮기다.
편의점은 전국적으로 약 5만 5천여 개에 이르는 대표적인 오프라인 유통 채널입니다.
하지만 특정 상품의 빠른 품절, 한정 이벤트 상품(예: 포켓몬빵) 구매 실패, 높은 점포 밀집도에 따른 소비자 동선 낭비 등의 문제가 끊임없이 발생하고 있습니다.

POP:CON은 이런 문제를 해결하기 위해 만들어진 온라인 편의점 쇼핑몰입니다.

단순한 제품 판매를 넘어,
- 편의점 인기 상품 정보 제공
- 실시간 재고 기반 구매 추천
- 이벤트 상품 알림
- 편리한 온라인 주문 및 배송 기능까지

소비자 중심의 편의점 쇼핑 환경을 구현하는 것을 목표로 합니다.

이 프로젝트는 오프라인 중심 유통 구조의 한계를 온라인 플랫폼으로 극복하고자 한 실질적 시도였으며,
Spring Boot + MySQL 기반의 백엔드와 실사용을 고려한 UI/UX 설계를 통해 완성도를 높였습니다.

---

## 📌 프로젝트 개요

| 항목      | 내용                                                       |
| ------- | -------------------------------------------------------- |
| 프로젝트명   | POP\:CON (Pop + Convenience Store)                       |
| 개발 기간   | 4주                                                       |
| 프로젝트 형태 | 웹 기반 쇼핑몰 시스템                                             |
| PPT | 📊 [PPT 링크](https://docs.google.com/presentation/d/1BxEpcDTjkgh8fkRzs9a1IdSsEe2Q-FVK/edit?usp=sharing&ouid=103340559708893338520&rtpof=true&sd=true)|
| 시연영상 |🎥 [시연 영상 링크](https://drive.google.com/file/d/1i92APimE-gtBhlFISEcNDg3OFubHU7iC/view?usp=sharing)    |
| 핵심 키워드  | 장바구니, 찜목록, 결제, 냉장고 보관, 지도기반 검색, 고객센터                     |



## 📸 대표 이미지 및 시연

<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/b124c00f-76ca-4876-baca-33f1433e555e" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/997f5216-9dba-4d5b-b405-46e50df31da9" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/4f8778c9-d827-4e47-a8e2-38afd35c4689" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/e9557d7b-7638-4410-9ae1-d5cdde330eb8" />




---


---

## 👥 팀원

* 김기윤
* 정재윤
* 김동우
* 이승수
* 황장근
* 최번영

---

## 📄 목차

* [요구사항 정의서](#-요구사항-정의서)
* [기능 명세서](#-기능-명세서)
* [비기능 명세서](#-비기능-명세서)
* [주요 기능 설명](#-주요-기능-설명)
* [기술 스택](#-기술-스택)
* [시스템 구조](#-시스템-구조)
* [ERD](#-erd)
* [향후 개선사항](#-향후-개선사항)

---

## 📋 요구사항 정의서

### ✅ 사용자 요구사항

* 회원가입 및 로그인 가능해야 한다.
* 상품을 장바구니에 담고 수량을 조절할 수 있어야 한다.
* 결제 기능이 안정적으로 작동해야 한다.
* 편의점 위치 기반 상품 검색이 가능해야 한다.
* 주문 이력 및 냉장고(임시보관) 기능이 있어야 한다.
* 고객센터 문의/FAQ 시스템이 있어야 한다.

### ✅ 관리자 요구사항

* 모든 회원의 정보를 열람 가능해야 한다.
* FAQ, QnA에 답변을 작성할 수 있어야 한다.

---

## 📌 기능 명세서

| 기능명    | 설명                 | API                               |
| ------ | ------------------ | --------------------------------- |
| 회원가입   | 주소 API 연동 포함       | `POST /signup`                    |
| 로그인    | JWT 기반 인증          | `POST /authenticate`              |
| 장바구니   | 수량 조절 / 삭제 / 결제 전송 | `GET/POST/DELETE /cart/...`       |
| 찜목록    | 추가/삭제 및 장바구니 이동    | `GET/POST/DELETE /wish/...`       |
| 냉장고    | 재고 부족 시 상품 보관      | `GET/POST /keep/...`              |
| 결제     | PortOne 연동 / 주문 처리 | `POST /orders/place`              |
| 주문 조회  | 페이징 처리 / 상세조회      | `GET /orders/user/{id}`           |
| 지도검색   | 카카오지도 + 현재위치 + 편의점 | 외부 API (Kakao Maps)               |
| 1:1 문의 | 문의 등록 및 조회         | `POST /ask`, `GET /myinquiry/...` |
| FAQ    | 전체조회 / 관리자 등록      | `GET /faq`, `POST /faq`           |
| 관리자 답변 | QnA 답변 추가          | `POST /qna/answer/...`            |

---

## 📂 비기능 명세서

| 항목     | 내용                                    |
| ------ | ------------------------------------- |
| 인증 보안  | JWT + Spring Security, httpOnly 지원 가능 |
| 암호화    | BCrypt (비밀번호 암호화)                     |
| 결제 안정성 | PortOne 연동, 결제 실패 시 로직 존재             |
| API 방식 | RESTful API                           |
| 응답 포맷  | JSON, DTO 통일                          |
| 에러 처리  | 응답코드 + 에러 메시지 구조화                     |
| 반응성    | PC 대응 기준 (모바일 미구현)                    |
| 성능     | 주문/찜/보관/FAQ 등 각 기능 비동기 처리 구현됨         |

---

## 💡 주요 기능 설명

* **로그인/회원가입**: JWT 토큰 기반 인증, 다음 주소 검색 API 연동
* **장바구니/찜/냉장고**: 수량 관리 + 이동 가능, 재고 부족 시 냉장고 이동 처리
* **결제**: 포트원 API로 카드 결제, 결제 후 장바구니 초기화 + 주문 DB 저장 + 냉장고 이동
* **편의점 지도 검색**: 카카오 지도 기반 거리 계산, 마커 생성, 반경 그리기, 정렬까지 구현
* **문의/FAQ**: 1:1문의 등록 및 관리자 응답 / FAQ 카테고리별 아코디언

---

## 🧱 기술 스택

### 백엔드

* Java 8 / Spring Boot 3
* Spring Security + JWT
* JPA + MyBatis
* PortOne (결제)
* MySQL

### 프론트엔드

* React 18
* React Router DOM
* Axios
* Kakao 지도 API / 다음 주소 API
* PortOne JavaScript SDK

---

## 🧭 시스템 구조

<img width="856" height="597" alt="image" src="https://github.com/user-attachments/assets/1290049e-8f7c-4e73-b123-3b606410df9a" />


---

## 🧾 ERD

<img width="3410" height="1183" alt="Project_PopCon" src="https://github.com/user-attachments/assets/028614bb-b440-4bf1-852e-d02eff25d846" />


---



## 🚧 향후 개선사항

* 🗣️ 챗봇 기능 (계획됨)
* 📱 모바일 반응형 적용
* 📦 배송 트래킹 기능
* 🧾 쿠폰, 포인트 시스템
* 🔍 OpenSearch 기반 고속 검색 기능 고도화

---


> 본 프로젝트는 **직접 쇼핑몰의 CRUD, 인증, 결제, API 연동을 구현**하며 팀 협업을 바탕으로 구축되었습니다.

## 📒 작업 노션 링크

> [📝 프로젝트 Notion 보드 바로가기](https://tabby-roarer-f4c.notion.site/Project-Popcon-8b8a31c7b1564994be083611ea3dd8aa)
