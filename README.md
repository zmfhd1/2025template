# [2025년 한이음 드림업] README_SAMPLE 📝

- README 파일 작성시, 아래 5가지 항목 내용은 필수로 작성해야 합니다.
- 아래 항목이외에 이해를 돕기위한 내용을 자유롭게 추가해도 됩니다.
---

## **1. 프로젝트 소개**
- **프로젝트 명** : 한이음 드림업 AI검색 서비스
- **한줄 소개** : AI 기반 맞춤형 검색 서비스를 통해 사용자가 원하는 데이터를 빠르고 효율적으로 탐색
- **기대 효과** : 검색 엔진을 다양한 도메인(논문, 뉴스, 제품 정보 등)으로 확장할 수 있어, 다양한 산업 분야 적용 가능성 확보
- **개발 환경** : 검색 엔진을 다양한 도메인(논문, 뉴스, 제품 정보 등)으로 확장할 수 있어, 다양한 산업 분야 적용 가능성 확보

---

## **2. 팀 소개**
<table>
  <tr>
    <td align="center" width="150">
      <img src="https://github.com/user-attachments/assets/334045b4-4c1d-41e0-9953-c078488ea76f" width="120" height="120" style="border-radius:10px; box-shadow:2px 2px 8px rgba(0,0,0,0.2);"><br>
      <b>홍길동</b><br>
      ㅇㅇ대학교<br>
      • 개발총괄<br>
      • UI/UX 기획
    </td>
    <td align="center" width="150">
      <img src="https://github.com/user-attachments/assets/044c022d-aefb-415e-bdc6-af4d6b0938af" width="120" height="120" style="border-radius:10px; box-shadow:2px 2px 8px rgba(0,0,0,0.2);"><br>
      <b>한이음</b><br>
      ㅇㅇ대학교<br>
      • 백엔드<br>
      • 프론트엔드
    </td>
    <td align="center" width="150">
      <img src="https://github.com/user-attachments/assets/69f6a559-ce87-478c-975c-dfb377996e58" width="120" height="120" style="border-radius:10px; box-shadow:2px 2px 8px rgba(0,0,0,0.2);"><br>
      <b>김지수</b><br>
      ㅇㅇ대학교<br>
      • API 개발<br>
      • DB 서버 구축
    </td>
    <td align="center" width="150">
      <img src="https://github.com/user-attachments/assets/334045b4-4c1d-41e0-9953-c078488ea76f" width="120" height="120" style="border-radius:10px; box-shadow:2px 2px 8px rgba(0,0,0,0.2);"><br>
      <b>이철수</b><br>
      ㅇㅇ대학교<br>
      • 데이터 분석<br>
      • 전처리
    </td>
  </tr>
</table>




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
