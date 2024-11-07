---
title: "[졸작] AWS 캠핑장 데이터 처리(2) - RDS 성능 향상"
date: 2024-11-04 23:00:00 +0900
categories: [Project, 졸업작품]
tags: [JAVA, 자바, 안드로이드, 어플, 캠핑장]
---

# 💡 AWS RDS로 MySQL 구축하기

### 👉 RDS에서 데이터베이스 인스턴스 생성

```java
@GetMapping("/basedList")
    public ResponseEntity<List<GoCampingItemDto>> baseSearch() throws IOException {
        JSONArray jsonArray = goCampingService.baseSearch();
        List<GoCampingItemDto> dtos = new ArrayList<>();
        for (int i = 0; i < jsonArray.length(); i++) {
            JSONObject jsonObject = jsonArray.getJSONObject(i);
            GoCampingItemDto dto = new GoCampingItemDto();
            goCampingService.setDtoFields(dto, jsonObject);
            dtos.add(dto);
            campsiteService.saveCampsite(dto);
        }
        return ResponseEntity.ok(dtos);
    }
```
