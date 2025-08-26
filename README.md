# [2025년 한이음 드림업] README_SAMPLE 📝

- README 파일 작성시, 아래 5가지 항목 내용은 필수로 작성해야 합니다.
- 아래 항목이외에 이해를 돕기위한 내용을 자유롭게 추가해도 됩니다.
---

## **1. 프로젝트 소개**
1-1. 프로젝트 개요
- 프로젝트 명 : 한이음 드림업 AI검색 서비스
- 한줄 소개 : 사용자의 검색 의도를 이해하고 최적의 정보를 제공하는 AI 기반 맞춤형 검색 서비스

1-2. 기대 효과 및 활용 분야
- 기대 효과 : 검색 품질 향상 및 정보 탐색 효율 극대화, 다양한 산업 분야에서 데이터 활용성 확대
- 활용 분야 : 학술·연구, 커머스·쇼핑, 헬스케어, 뉴스·미디어, 기업 내부 문서 검색 등

1-3. 기술 스택
- 프론트엔드 : React, Next.js, Tailwind CSS
- 백엔드 : Python(FastAPI), Node.js, Django
- AI/ML : PyTorch, TensorFlow, Hugging Face, OpenAI API
- 데이터베이스 : PostgreSQL, MongoDB, Elasticsearch
- 클라우드 : AWS
- 배포 및 관리 : Docker, Kubernetes, GitHub Actions

---

## **2. 팀 소개**
| <img src="https://github.com/user-attachments/assets/334045b4-4c1d-41e0-9953-c078488ea76f" width="100" height="100"> | <img src="https://github.com/user-attachments/assets/044c022d-aefb-415e-bdc6-af4d6b0938af" width="100" height="100"> | <img src="https://github.com/user-attachments/assets/69f6a559-ce87-478c-975c-dfb377996e58" width="100" height="100"> | <img src="https://github.com/user-attachments/assets/334045b4-4c1d-41e0-9953-c078488ea76f" width="100" height="100"> | <img src="https://github.com/user-attachments/assets/044c022d-aefb-415e-bdc6-af4d6b0938af" width="100" height="100"> |
|:---:|:---:|:---:|:---:|:---:|
| **홍길동** | **한이음** | **최지수** | **이철수** | **김멘토** |
| ○○대학교 <br> • 개발총괄 <br> • UI/UX 기획 | ○○대학교 <br> • 백엔드 <br> • 프론트엔드 | ○○대학교 <br> • API 개발 <br> • DB 서버 구축 | ○○대학교 <br> • 데이터 분석 <br> • 전처리 | ○○전자 <br> • 프로젝트 멘토 <br> • 기술 자문 |



---
## **3. 시스템 구성도**
> **참고** S/W구성도, H/W구성도, 서비스흐름도 등을 전체적으로 작성(그림을 포함한 도식 또는 흐름으로 표현)
<img alt="image" src="https://github.com/user-attachments/assets/28fc8453-d1a0-4184-8fd0-130d93d18545" />

---
## **4. 작품 소개영상**
```
아래와 같이 작성하면, 썸네일과 링크등록을 할 수 있습니다.
[![영상 제목](유튜브 썸네일 URL)](유튜브 영상 URL)

작성 예시 : 저는 다음과 같이 작성하니, 아래와 같이 링크가 연결된 썸네일 이미지가 등록되었네요! 
[![한이음 드림업 프로젝트 소개](https://github.com/user-attachments/assets/16435f88-e7d3-4e45-a128-3d32648d2d84)](https://youtu.be/YcD3Lbn2FRI?si=isERqIAT9Aqvdqwp)
```
[![한이음 드림업 프로젝트 소개](https://github.com/user-attachments/assets/16435f88-e7d3-4e45-a128-3d32648d2d84)](https://youtu.be/YcD3Lbn2FRI?si=isERqIAT9Aqvdqwp)


---

## **5. 핵심 소스코드**
**참고** API를 활용해서 자동 배포(Deployment)를 생성하는 기능을 담당하는 메서드
```java
    private static void start_deployment(JsonObject jsonObject) {
        String user = jsonObject.get("user").getAsJsonObject().get("login").getAsString();
        Map<String, String> map = new HashMap<>();
        map.put("environment", "QA");
        map.put("deploy_user", user);
        Gson gson = new Gson();
        String payload = gson.toJson(map);

        try {
            GitHub gitHub = GitHubBuilder.fromEnvironment().build();
            GHRepository repository = gitHub.getRepository(
                    jsonObject.get("head").getAsJsonObject()
                            .get("repo").getAsJsonObject()
                            .get("full_name").getAsString());
            GHDeployment deployment =
                    new GHDeploymentBuilder(
                            repository,
                            jsonObject.get("head").getAsJsonObject().get("sha").getAsString()
                    ).description("Auto Deploy after merge").payload(payload).autoMerge(false).create();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```
