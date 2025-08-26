# [2025년 한이음 드림업] README_SAMPLE 📝

- README 파일 작성시, 아래 5가지 항목 내용은 필수로 작성해야 합니다.
- 아래 항목이외에 이해를 돕기위한 내용을 자유롭게 추가해도 됩니다.
- README_SAMPLE.md 이 단순한 형태의 예제이니 참고하세요.
---

## **1. 프로젝트 소개**
- **프로젝트명** : 한이음 드림업 AI검색 서비스
- **팀명** : 드리미
- **팀번호** : `25_HC001`
- **한줄 소개** : AI 기반 맞춤형 검색 서비스를 통해 사용자가 원하는 데이터를 빠르고 효율적으로 탐색

---

## **2. 팀원 소개**
(이름, 소속, 역할 기재)
- 홍길동, ㅇㅇ대학교, 총괄
- 한이음, ㅇㅇ대학교, 백엔드
- 김이음, ㅇㅇ대학교, 프론트엔드
- 최이음, ㅇㅇ대학교, 기획, UI/UX

---
## **3. 시스템 구성도**
한이음 드림업 프로젝트는 창의도전형, 학점연계형(사회공헌/여성참여)로 구성되어 있습니다.
<img alt="image" src="https://github.com/user-attachments/assets/28fc8453-d1a0-4184-8fd0-130d93d18545" />

---
## **4. 핵심 소스코드**

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

---
## **5. 작품 소개영상**
```
아래와 같이 작성하면, 썸네일과 링크등록을 할 수 있습니다.
[![영상 제목](유튜브 썸네일 URL)](유튜브 영상 URL)

작성 예시 : 저는 다음과 같이 작성하니, 아래와 같이 링크가 연결된 썸네일 이미지가 등록되었네요! 
[![한이음 드림업 프로젝트 소개](https://github.com/user-attachments/assets/16435f88-e7d3-4e45-a128-3d32648d2d84)](https://youtu.be/YcD3Lbn2FRI?si=isERqIAT9Aqvdqwp)
```
[![한이음 드림업 프로젝트 소개](https://github.com/user-attachments/assets/16435f88-e7d3-4e45-a128-3d32648d2d84)](https://youtu.be/YcD3Lbn2FRI?si=isERqIAT9Aqvdqwp)


---
