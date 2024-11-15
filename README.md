
# 한국어 불용어 사전 (Korean Stopwords Dictionary)

이 저장소는 한국어 텍스트 전처리에 유용한 **한국어 불용어 사전**을 제공합니다. 불용어는 텍스트 분석 시 의미가 적거나 분석에 방해가 되는 단어들로, NLP(Natural Language Processing) 프로젝트에서 자주 제거됩니다. 이 사전은 **조사**, **접속사**, **관형사**, **감탄사**, **기타**의 다섯 가지 카테고리로 분류되어 있으며, 여러 파일 형식으로 제공하여 다양한 환경에서 손쉽게 사용할 수 있습니다.

## 파일 다운로드
- [stopwords_korean.txt](./stopwords_korean.txt): 카테고리별로 불용어를 분류한 텍스트 파일.
- [stopwords_korean.json](./stopwords_korean.json): 카테고리별로 불용어를 구조화한 JSON 파일.

## 카테고리
불용어는 의미적 역할에 따라 다섯 가지 카테고리로 분류됩니다.

1. **조사**: 주로 명사와 결합하여 문장 구조를 형성하는 요소. 예시: `가`, `의`, `으로`.
2. **접속사**: 문장과 문장을 연결하는 역할. 예시: `그리고`, `그러나`, `따라서`.
3. **관형사**: 명사 앞에서 수식하여 의미를 보충하는 역할. 예시: `여러`, `다른`, `특별한`.
4. **감탄사**: 감정을 표현하거나 대화를 시작하는 역할. 예시: `아`, `어`, `우와`.
5. **기타**: 위의 분류에 속하지 않지만 분석 시 제외할 필요가 있는 단어들. 예시: `거의`, `그냥`, `자주`.

## 설치 및 사용법
### 텍스트 파일 (`.txt`) 사용법
카테고리별로 나누어진 `updated_stopwords_kr.txt` 파일을 사용하여 Python이나 기타 언어에서 텍스트 파일을 불러와 사용하세요.

```python
# 텍스트 파일을 읽어 불용어 리스트로 사용하기
with open("updated_stopwords_kr.txt", "r", encoding="utf-8") as file:
    stopwords = [line.strip() for line in file if not line.startswith("#") and line.strip()]
print(stopwords)
```

### JSON 파일 (`.json`) 사용법
카테고리별로 불용어가 JSON 구조로 저장되어 있어, Python이나 다른 언어에서 JSON 파일을 로드하여 쉽게 사용할 수 있습니다.

```python
import json

# JSON 파일에서 불용어를 읽어오기
with open("updated_stopwords_kr.json", "r", encoding="utf-8") as file:
    stopwords = json.load(file)
    
# 특정 카테고리의 불용어 가져오기
print("조사 불용어:", stopwords["조사"])
print("감탄사 불용어:", stopwords["감탄사"])
```

## 데이터 구조
- **텍스트 파일**: 카테고리마다 구분되어 있으며, 카테고리 이름은 `#`으로 시작합니다. 각 단어는 줄 단위로 분리되어 있습니다.
- **JSON 파일**: 각 카테고리가 키가 되고, 불용어 리스트가 값으로 저장된 딕셔너리 구조입니다.

## 활용 예시
이 불용어 사전은 다양한 NLP 프로젝트에서 사용될 수 있으며, 주로 텍스트 분석, 감정 분석, 문서 분류, 토픽 모델링 등의 전처리 단계에서 활용됩니다.

### 불용어 필터링 예제
```python
def remove_stopwords(text, stopwords_dict):
    words = text.split()
    filtered_text = [word for word in words if word not in stopwords_dict["조사"]]
    return " ".join(filtered_text)

text = "이 텍스트는 예시로 작성되었습니다."
filtered_text = remove_stopwords(text, stopwords)
print(filtered_text)
```

## 기여 방법
- 이 프로젝트에 기여하고 싶다면 새로운 불용어를 추가하거나 수정 사항이 있을 때 Issue나 Pull Request를 남겨 주세요.

## 라이선스
이 저장소는 MIT 라이선스 하에 배포되며, 누구나 자유롭게 사용하고 수정할 수 있습니다.

## 문의
프로젝트 관련 문의 사항은 Issue를 통해 남겨 주시기 바랍니다.

---

이 불용어 사전이 한국어 NLP 프로젝트의 전처리 과정에 많은 도움이 되길 바랍니다!
