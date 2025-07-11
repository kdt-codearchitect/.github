# 🛒 POP\:CON - 온라인 편의점 쇼핑몰

> 편하게, 빠르게, 익숙하게. 대형 편의점을 집 앞까지 옮기다.

---

## 📌 프로젝트 개요

| 항목      | 내용                                                       |
| ------- | -------------------------------------------------------- |
| 프로젝트명   | POP\:CON (Pop + Convenience Store)                       |
| 개발 기간   | 4주                                                       |
| 프로젝트 형태 | 웹 기반 쇼핑몰 시스템                                             |
| 핵심 키워드  | 장바구니, 찜목록, 결제, 냉장고 보관, 지도기반 검색, 고객센터                     |



## 📸 대표 이미지 및 시연

<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/b124c00f-76ca-4876-baca-33f1433e555e" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/997f5216-9dba-4d5b-b405-46e50df31da9" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/4f8778c9-d827-4e47-a8e2-38afd35c4689" />
<img width="1920" height="1032" alt="image" src="https://github.com/user-attachments/assets/53be4e4d-5718-4614-9ed4-eeefe8518569" />







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

* [요구사항 정의서](#요구사항-정의서)
* [기능 명세서](#기능-명세서)
* [비기능 명세서](#비기능-명세서)
* [주요 기능 설명](#주요-기능-설명)
* [기술 스택](#기술-스택)
* [시스템 구조](#시스템-구조)
* [ERD](#erd)
* [실행 방법](#실행-방법)
* [향후 개선사항](#향후-개선사항)

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

> 프론트 → Axios → Spring Controller → Service → JPA + MyBatis → DB & 외부 API

(📷 아키텍처 PPT 이미지 삽입 가능)

---

## 🧾 ERD

> 고객, 장바구니, 주문, 찜목록, 냉장고, 문의, FAQ 등으로 구성됨

(📷 ERD 설계도 이미지 삽입 가능)

---



## 🚧 향후 개선사항

* 🗣️ 챗봇 기능 (계획됨)
* 📱 모바일 반응형 적용
* 📦 배송 트래킹 기능
* 🧾 쿠폰, 포인트 시스템
* 🔍 OpenSearch 기반 고속 검색 기능 고도화

---


> 본 프로젝트는 **직접 쇼핑몰의 CRUD, 인증, 결제, API 연동을 구현**하며 팀 협업을 바탕으로 구축되었습니다.

## 작업시 사용하던 노션
https://tabby-roarer-f4c.notion.site/Project-Popcon-8b8a31c7b1564994be083611ea3dd8aa

