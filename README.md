# ☁️ SmartCollab: Real-Time Cloud Collaboration Platform

**SmartCollab**은 클라우드 환경에서 개인의 파일을 안전하게 저장하고, 팀원들과 함께 실시간으로 문서를 편집하고 소통할 수 있는 차세대 협업 플랫폼입니다.  
이 프로젝트는 **Spring Boot**와 **React**를 기반으로 구축되었으며, **Microsoft Azure 클라우드 서비스**를 활용하여 안정적이고 확장 가능한 서비스를 제공합니다.

---

## ✨ Live Demo

🔗 [배포 주소 바로가기](https://@@@@@.azurewebsites.net)  


---

## 🚀 주요 기능 (Key Features)

SmartCollab은 개인 작업부터 팀 프로젝트까지 생산성을 극대화하기 위한 다양한 기능을 제공합니다.

| 기능 분류 | 상세 내용 |
| :--- | :--- |
| **📁 파일 및 폴더 관리** | • 개인/팀별 독립된 스토리지 공간 제공<br>• 파일/폴더 생성, 이름 변경, 이동, 복사, 삭제 등 CRUD 지원<br>• 직관적인 계층 구조(Breadcrumb)를 통한 탐색 |
| **🤝 팀 협업** | • 팀 생성 및 사용자 초대 기능<br>• 멤버별 권한 관리 (수정, 삭제, 초대, 팀장 위임)<br>• 팀 삭제 및 팀 나가기 기능 |
| **💬 실시간 채팅 및 알림** | • 팀 전용 실시간 채팅방 제공 (WebSocket 기반)<br>• 다른 팀의 새 메시지에 대한 '안 읽음' 표시 기능<br>• 팀 초대/권한 변경 등 주요 활동에 대한 실시간 알림 |
| **📑 고급 문서 기능** | • **파일 버전 관리**: 변경 이력 자동 저장 및 특정 버전 복원<br>• **파일 미리보기**: 이미지, PDF, MS Office 문서(docx, pptx, xlsx) 미리보기<br>• **AI 기능**: DeepL API를 활용한 실시간 번역 및 요약 |
| **🔗 안전한 파일 공유** | • 파일 공유용 고유 링크 생성<br>• 비밀번호 설정 및 만료 기간 지정 |
| **🔐 보안 및 인증** | • JWT(JSON Web Token) 기반 사용자 인증<br>• Spring Security 기반 API 접근 제어 |

---

## 🛠️ 기술 스택 (Tech Stack)

| 구분 | 기술 | 설명 |
| :--- | :--- | :--- |
| **Backend** | `Java 17`, `Spring Boot 3.2.5` | 안정적이고 빠른 서버 개발 |
| | `Spring Data JPA` | MySQL과 객체지향적 연동 |
| | `Spring Security`, `JWT` | 인증/인가 시스템 구축 |
| | `Spring WebSocket (STOMP)` | 실시간 양방향 통신 |
| **Frontend** | `React 18` (CDN) | 컴포넌트 기반 UI/UX |
| | `JavaScript (ES6+)`, `Babel` | 최신 문법 사용 |
| | `Tailwind CSS` | Utility-First 스타일링 |
| **Database** | `MySQL 8.0` | 관계형 데이터베이스 |
| **Cloud** | `Microsoft Azure` | App Service(애플리케이션 호스팅), Blob Storage(파일 저장) |
| **API** | `DeepL API` | 고품질 기계 번역 |
| **Build Tool** | `Gradle` | 의존성 관리 및 빌드 |

---

## 🏗️ 시스템 아키텍처 (System Architecture)

1. **Client (React SPA)**: 사용자는 웹 브라우저를 통해 React 기반 SPA와 상호작용합니다.
2. **Web Server (Azure App Service)**: Spring Boot 애플리케이션이 Azure App Service 위에서 실행됩니다.  
   - **REST API**: 파일/폴더 관리, 팀 관리 등 대부분의 기능 처리  
   - **WebSocket**: 실시간 채팅 및 알림 처리
3. **Database (MySQL)**: 사용자 정보, 파일 메타데이터, 팀 정보 저장
4. **File Storage (Azure Blob Storage)**: 파일 원본 및 버전 데이터 저장.  
   - 파일 복사 시 **SAS(Shared Access Signature) URL**을 활용하여 효율적으로 처리

---

## 📖 데이터베이스 스키마 (ERD)

- **User**: 모든 활동 주체 (팀 생성/참여)  
- **Team & TeamMember**: 사용자와 팀의 다대다 관계 및 권한 관리  
- **Folder & FileEntity**: 계층 구조 기반 폴더/파일 관리 (개인 폴더=team_id NULL, 팀 폴더=team_id 값 존재)  
- **FileVersion**: 파일의 다중 버전 관리 (`activeVersion`으로 현재 버전 지정)  
- **Invitation & Notification**: 팀 초대와 결과 알림 처리  

---

## ⚙️ 시작하기 (Getting Started)

### Prerequisites
- Java 17 (JDK)  
- Gradle 8.x  
- MySQL 8.0  
- IntelliJ IDEA 또는 VS Code

### Backend 실행

1. **Git 저장소 복제**
   ```bash
   git clone https://github.com/your-username/smartcollab-prod.git
   cd smartcollab-prod
