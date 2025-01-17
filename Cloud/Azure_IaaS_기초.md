# 가상머신 배포 고려사항

## 가상 머신 이름과 호스트 이름

- 가상 머신 이름 변경 불가 -> 호스트이름 변경가능
- 이름 규칙 : 환경, 위치, 역할, 인스턴스 번호

## 배포 위치와 비용

- 실제 사용자 위치
- 법, 규정준수 세금
- 위치에 따른 다른 사용 가능한 VM 크기
- 동일한 VM 크기, 위치에 따른 다른 가격

## Azure 서비스의 리소스 생성 모델

- 하위 리소스(원시 부품)
- 상위 리소스(모듈)
- 서비스(최종 제품)
- -> 레고 블럭 모델

## Azure 가상 머신 구성 요소

1. 운영체제
2. 네트워킹 요소
3. 가상 머신 크기(os.vhd)
4. 가상 디스크

## 가상 머신 크기 형식

- 범용 : CPU 대 메모리 비율이 적당
- 컴퓨팅 최적화 : CPU 대 메모리 비율이 높음
- 메모리 최적화 : 메모딜 대 CPU 배율이 높음
- Storage에 최적화 : 높은 디스크 처리량 및 I/O
- GPU : 대량의 그래픽 렌더링 및 비디오 편집에 적합한 전문 가상 머신
- 고성능 컴퓨팅 : 가장 빠르고 강력한 CPU 가상 머신

## 스토리지에서 크시

- GiB != GB (기비바이트와 기가바이트는 다르다)
- TiB != TB
- 1000KB = 1MB
- 1024KB = 1MiB

## Azure 스토리지 개요

### 데이터 유형

- 비정형 데이터(비 구조적 데이터) ex. 사진, 영상, 오디오 ...
- 반정형 데이터(반 구조적 데이터) ex. json, xml -> Nosql
- 정형 데이터(구조적 데이터) ex. sql

## 파일 공유 개요

### 특징

1. SMB프로토콜을 사용하는 데 관리되는 파일 공유
2. SAS토큰을 포함하는 URL을 통한 안전한 엑세스
3. 표준파일 공유와 프리미엄 파일 공유

# 컨테이너 스토리지 서비스

## Blob Storage

- 클라우드에 구조화되지 않은 데이터 저장
- 모든 텍스트 또는 이진 데이터 형식 저장
- 개체 스토리지라고도 함
- 일반적인 용도
  - 브라우저에 직접 이미지 또는 문서 제공
  - 분산 엑세스용 파일 저장
  - 비디오 및 오디오 스트리밍
  - 백업 및 복원, 재해복구, 보관용으로 데이터 저장
- 스토리지 -> 컨테이너 -> Blob

## Azure Blob 계층

- 핫계층 : 자주 엑세스하거나 수정되는 데이터
- 쿨계층 : 드물게 엑세스되고 최소 30일 동안 저장되는 데이터에 최적화
- 콜드계층 : 90일 이상 드물게 엑세스되거나 또는 수정 및 저장되지 않는 데이터
- 보관 : 검색 대기 시간에 몇 시간 이상씩 걸리며, 최소 180일 이상 보관 계층에 저장되는 데이터

## 스냅샷

- 애플리케이션 오류 및 데이터 손상으로부터 보호
- 실수로 삭제 또는 의도하지 않은 변경 방지
- 백업 및 복구 지원
