# PAYCO 가맹점 정리

## 기존 기능 분석

### PAYCO - 식권 사용처 보기

- 가맹점의 위치와 이름만 제공하기 때문에, 해당 식당에서 제공하는 음식을 확인하는 것이 불편함
- 식당 이름을 클릭하면 네이버 상세보기 페이지가 열리지만, 새 창이 뜨고 로딩 속도 때문에 여러 식당을 빠르게 확인하기에는 번거로움

### 사내 웹 사이트 - [오늘 뭐 먹지?](https://alpha-food.cloud.ncsoft.com)

- 간단한 약도로 식당 위치를 표시하지만, 건물 내 몇 층에 있는지 등의 정보가 없어 방문 시 추가 검색이 필요함
- 새로운 가맹점이 추가되거나 기존 가맹점이 삭제될 경우, 운영자가 직접 정보를 수정해야 함
- 자세한 식당 메뉴를 확인할 수 없고, 음식이나 내부 사진은 사용자들이 직접 업로드해야 하므로 다양한 정보를 얻기 어려움
- 사내 인원만 이용 가능해 리뷰가 적음

## 차별점

- 식당 위치, 음식 메뉴, 실제 리뷰를 한 번에 확인할 수 있음
- PAYCO API를 기반으로 제작되어, 가맹점 정보가 변경되어도 운영자가 별도로 정보를 업데이트할 필요가 없음
- 네이버에서 사진과 리뷰 정보를 크롤링 해오기 때문에 사내 유저들의 정보에 의존할 필요가 없음

## 개발 방법

### 판교 식권존 호출 API

[PAYCO │ 페이코 라이프 하세요](https://www.payco.com/partner/offline.nhn?currentPage=1&tagNames=&categoryKey=CATG200004)

- 판교 PAYCO 식권 사용 가능한 가맹점 정보를 불러올 때 사용
- **Request**
    
    ```bash
    curl -i -X GET \
     'https://partner.payco.com/merchant/search/offline/detail/list?currentPage=1&perPage=15&partnerType=PAYCOZONE&partnerCode=BIZ_PANGYO&searchWord'
    ```
    
- **Response**
    
    ```json
    {
        "partnerList": [
            {
                "partnerAddress": "경기도 성남시 분당구 판교대장로7길 16-6 (대장동) 1층 ",
                "partnerCode": "POTT6F",
                "partnerMobileUrl": "https://m.place.naver.com/restaurant/1098691608/home",
                "chnlTagInfo": "MEAL,PAYCO_POINT",
                "paycoZoneCodeList": "BIZ_PANGYO",
                "categoryName": "기타",
                "tagInfo": "식권 PAYCO포인트",
                "ratingScore": 0,
                "chnlType": "OFFLINE",
                "closeTime": "",
                "openTime": "",
                "backgroundImgUrl": "",
                "viewDepth": 2,
                "introWord": "",
                "partnerName": "우리한우곰탕",
                "partnerUrl": "",
                "merchantCount": 0,
                "categoryKey": "CATG200018",
                "customerCenterUrl": "",
                "biAppImgUrl": "",
                "detailCategoryKey": "CATG200018D012",
                "keyWord": "",
                "completeYmdt": "2023-10-18T11:18:51",
                "biImgUrl": "",
                "detailCategoryName": "기타",
                "pgKey": "PAYCO",
                "franchiseCode": "SELFOPEN",
                "location": "37.3715031,127.0689091",
                "partnerType": "MERCHANT",
                "searchRegYmdt": "2024-07-26T15:07:08",
                "rank": 1,
                "distance": 2.3,
                "customerCenterEmail": "test@test.com",
                "telNumber": "031-717-5955"
            },
            {
                "partnerAddress": "경기도 성남시 분당구 대왕판교로 255 1층(궁내동) ",
                "partnerCode": "NKJJXR",
                "partnerMobileUrl": "https://m.place.naver.com/restaurant/1266519672/home",
                "chnlTagInfo": "PAYCO_POINT,MEAL",
                "paycoZoneCodeList": "BIZ_PANGYO",
                "categoryName": "식권",
                "tagInfo": "PAYCO포인트 식권",
                "ratingScore": 0,
                "chnlType": "OFFLINE",
                "closeTime": "",
                "openTime": "",
                "backgroundImgUrl": "",
                "viewDepth": 2,
                "introWord": "",
                "partnerName": "생선가게(사카나야)",
                "partnerUrl": "https://www.payco.com",
                "merchantCount": 0,
                "categoryKey": "CATG200004",
                "customerCenterUrl": "",
                "biAppImgUrl": "https://image.toast.com/aaaaac/paycoBi/appBi_1552453986317.png",
                "detailCategoryKey": "CATG200004D007",
                "keyWord": "",
                "completeYmdt": "2021-10-27T10:41:37",
                "biImgUrl": "",
                "detailCategoryName": "일식",
                "pgKey": "PAYCO",
                "franchiseCode": "BIZ_ETC",
                "location": "37.3666437,127.1010361",
                "partnerType": "MERCHANT",
                "searchRegYmdt": "2024-07-26T15:06:45",
                "rank": 2,
                "distance": 2.3,
                "customerCenterEmail": "test@test.com",
                "telNumber": "031-702-0300"
            },
            {
                "partnerAddress": "경기도 성남시 분당구 대왕판교로 387 (백현동) 2층 ",
                "partnerCode": "BFRB2M",
                "partnerMobileUrl": "",
                "chnlTagInfo": "MEAL",
                "paycoZoneCodeList": "BIZ_PANGYO",
                "categoryName": "기타",
                "tagInfo": "식권",
                "ratingScore": 0,
                "chnlType": "OFFLINE",
                "closeTime": "",
                "openTime": "",
                "backgroundImgUrl": "",
                "viewDepth": 2,
                "introWord": "",
                "partnerName": "풍년맛집",
                "partnerUrl": "",
                "merchantCount": 0,
                "categoryKey": "CATG200018",
                "customerCenterUrl": "",
                "biAppImgUrl": "",
                "detailCategoryKey": "CATG200018D012",
                "keyWord": "",
                "completeYmdt": "2023-05-23T10:00:30",
                "biImgUrl": "",
                "detailCategoryName": "기타",
                "pgKey": "PAYCO",
                "franchiseCode": "SELFOPEN",
                "location": "37.3783328,127.1022399",
                "partnerType": "MERCHANT",
                "searchRegYmdt": "2024-07-26T15:07:04",
                "rank": 3,
                "distance": 2.3,
                "customerCenterEmail": "test@test.com",
                "telNumber": "03180171246"
            },
            {
                "partnerAddress": "경기도 성남시 분당구 판교역로 166 백현동, 카카오 판교 아지트 1층 14호 ",
                "partnerCode": "OY231T",
                "partnerMobileUrl": "https://m.place.naver.com/restaurant/1470046813/home",
                "chnlTagInfo": "MEAL,PAYCO_POINT",
                "paycoZoneCodeList": "BIZ_PANGYO",
                "categoryName": "식권",
                "tagInfo": "식권 PAYCO포인트",
                "ratingScore": 0,
                "chnlType": "OFFLINE",
                "closeTime": "",
                "openTime": "",
                "backgroundImgUrl": "",
                "viewDepth": 2,
                "introWord": "",
                "partnerName": "주식회사 펠트",
                "partnerUrl": "https://www.payco.com",
                "merchantCount": 0,
                "categoryKey": "CATG200004",
                "customerCenterUrl": "",
                "biAppImgUrl": "https://image.toast.com/aaaaac/paycoBi/appBi_1552453986317.png",
                "detailCategoryKey": "CATG200004D001",
                "keyWord": "",
                "completeYmdt": "2023-12-13T09:53:11",
                "biImgUrl": "",
                "detailCategoryName": "패스트푸드",
                "pgKey": "PAYCO",
                "franchiseCode": "BIZ_ETC",
                "location": "37.3793356,127.1060411",
                "partnerType": "MERCHANT",
                "searchRegYmdt": "2024-10-11T05:36:52",
                "rank": 4,
                "distance": 2.3,
                "customerCenterEmail": "test@test.com",
                "telNumber": "010-7112-7302"
            },
            {
                "partnerAddress": "경기도 성남시 분당구 판교로227번길 6 브릿지 타워 1층 116,117호",
                "partnerCode": "G93CK0",
                "partnerMobileUrl": "https://m.place.naver.com/restaurant/38780163",
                "chnlTagInfo": "MEAL,PAYCO_POINT",
                "paycoZoneCodeList": "BIZ_PANGYO",
                "categoryName": "식권",
                "tagInfo": "식권 PAYCO포인트",
                "ratingScore": 336,
                "chnlType": "OFFLINE",
                "closeTime": "",
                "openTime": "",
                "backgroundImgUrl": "https://image.toast.com/aaaaac/OnOffLine/판교존.jpg",
                "viewDepth": 2,
                "introWord": "",
                "partnerName": "최고야 전국5대짬뽕",
                "partnerUrl": "http://www.payco.com",
                "merchantCount": 0,
                "categoryKey": "CATG200004",
                "customerCenterUrl": "",
                "biAppImgUrl": "https://image.toast.com/aaaaac/paycoBi/appBi_1552453986317.png",
                "detailCategoryKey": "CATG200004D008",
                "keyWord": "",
                "completeYmdt": "2018-05-02T17:33:59",
                "biImgUrl": "https://image.toast.com/aaaaac/mrcbi/webBi_20180515113557.png",
                "detailCategoryName": "중식",
                "pgKey": "PAYCO",
                "franchiseCode": "ZONE_PANGYO_BIZ",
                "location": "37.4030095,127.0992527",
                "partnerType": "MERCHANT",
                "searchRegYmdt": "2024-07-26T15:06:12",
                "rank": 5,
                "distance": 2.3,
                "customerCenterEmail": "",
                "telNumber": "031-8017-8464"
            }
        ],
        "pageInfo": {
            "perPage": 5,
            "nextPage": "true",
            "totalCount": 376,
            "currentPage": 1
        },
        "maxDistance": "20000"
    }
    ```
    

### 네이버 Map API

[Web Dynamic Map API](https://guide.ncloud-docs.com/docs/maps-web-sdk)

- 식당 위치를 매핑할 지도 뷰를 위해 사용

### 네이버 Geocoding API

[Geocoding API](https://api.ncloud-docs.com/docs/ai-naver-mapsgeocoding-geocode)

- 주소로부터 지도 상에 표시할 x, y 값 가져올 때 사용
- **Request**
    
    ```bash
    curl --location --request GET 'https://naveropenapi.apigw.ntruss.com/map-geocode/v2/geocode?query=분당구 불정로 6' \
    --header 'x-ncp-apigw-api-key-id: {API Key ID}' \
    --header 'x-ncp-apigw-api-key: {API Key}' \
    --header 'Accept: application/json'
    ```
    
- **Response**
    
    ```json
    {
        "status": "OK",
        "meta": {
            "totalCount": 1,
            "page": 1,
            "count": 1
        },
        "addresses": [
            {
                "roadAddress": "경기도 성남시 분당구 불정로 6 NAVER그린팩토리",
                "jibunAddress": "경기도 성남시 분당구 정자동 178-1 NAVER그린팩토리",
                "englishAddress": "6, Buljeong-ro, Bundang-gu, Seongnam-si, Gyeonggi-do, Republic of Korea",
                "addressElements": [
                    {
                        "types": [
                            "SIDO"
                        ],
                        "longName": "경기도",
                        "shortName": "경기도",
                        "code": ""
                    },
                    {
                        "types": [
                            "SIGUGUN"
                        ],
                        "longName": "성남시 분당구",
                        "shortName": "성남시 분당구",
                        "code": ""
                    },
                    {
                        "types": [
                            "DONGMYUN"
                        ],
                        "longName": "정자동",
                        "shortName": "정자동",
                        "code": ""
                    },
                    {
                        "types": [
                            "RI"
                        ],
                        "longName": "",
                        "shortName": "",
                        "code": ""
                    },
                    {
                        "types": [
                            "ROAD_NAME"
                        ],
                        "longName": "불정로",
                        "shortName": "불정로",
                        "code": ""
                    },
                    {
                        "types": [
                            "BUILDING_NUMBER"
                        ],
                        "longName": "6",
                        "shortName": "6",
                        "code": ""
                    },
                    {
                        "types": [
                            "BUILDING_NAME"
                        ],
                        "longName": "NAVER그린팩토리",
                        "shortName": "NAVER그린팩토리",
                        "code": ""
                    },
                    {
                        "types": [
                            "LAND_NUMBER"
                        ],
                        "longName": "178-1",
                        "shortName": "178-1",
                        "code": ""
                    },
                    {
                        "types": [
                            "POSTAL_CODE"
                        ],
                        "longName": "13561",
                        "shortName": "13561",
                        "code": ""
                    }
                ],
                "x": "127.1054328",
                "y": "37.3595963",
                "distance": 0.0
            }
        ],
        "errorMessage": ""
    }
    ```
    

### 네이버 검색 API

[검색 > 지역 - Search API](https://developers.naver.com/docs/serviceapi/search/local/local.md#%EC%A7%80%EC%97%AD)

- 식당 정보 크롤링을 위해 사용

## 프로젝트 기대 효과

### 프론트엔드

- **React의 상태 관리 능력 향상**
    - 지도 API와의 상호작용, 위치 정보 및 식당 데이터의 동적 업데이트 등을 구현하면서, React의 상태 관리 툴(useState, useEffect, Redux … )을 효율적으로 사용
- **지도 API 통합 및 비동기 작업 처리 능력**
    - 네이버 지도 API를 연동하여 동적인 지도 뷰를 생성하고, API 호출 시 비동기 작업을 다루며 데이터를 효율적으로 렌더링
- **UI/UX 개선**
    - 사용자 친화적인 인터페이스를 구현
- **API 호출 및 에러 처리**
    - 네이버 지도 API나 백엔드 서버와 통신할 때, API 호출 실패나 비동기 작업의 에러를 효과적으로 처리

### 백엔드

- **Spring REST API 설계 및 개발 능력 향상**
    - 프론트엔드와 통신할 RESTful API를 설계하고, 안정적인 API 엔드포인트를 제공
- **웹 크롤링 경험**
    - 네이버나 다른 외부 서비스로부터 데이터를 크롤링하는 과정을 통해 크롤러 설계 능력 향상
- **API 성능 최적화 및 데이터 관리**
    - 외부 API와 웹 크롤링 데이터를 처리하는 과정에서 성능 이슈를 해결하고, Redis 캐시 활용 및 DB 설계 등 데이터를 효율적으로 관리
- **보안 및 데이터 무결성**
    - 크롤링 데이터와 API 통합 과정에서 발생할 수 있는 보안 문제 해결 및 데이터의 무결성을 유지
