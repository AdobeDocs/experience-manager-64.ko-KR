---
title: 초안 및 제출 데이터 서비스 사용자 정의
seo-title: Customizing Draft and Submission data services
description: AEM Forms은 기본적으로 게시 인스턴스의 기본 노드에 초안 및 제출된 적응형 양식을 저장합니다. 그러나 AEM Forms의 초안 및 제출 데이터 서비스를 구성하여 초안 및 제출된 적응형 양식의 저장소를 사용자 지정할 수 있습니다.
seo-description: AEM Forms, by default, stores draft and submitted adaptive forms in a default node on the Publish instance. However, you can configure the draft and submission data services of AEM Forms to customize the storage of draft and submitted adaptive forms.
uuid: c3ec1708-3b11-4142-93f0-1cffb6643f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 602fd6a9-9a65-411c-8475-a4082a3fdee0
exl-id: c6243a1f-8f8f-48dc-af3b-b165f451ce73
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 3%

---

# 초안 및 제출 데이터 서비스 사용자 정의 {#customizing-draft-and-submission-data-services}

>[!CAUTION]
>
>AEM 6.4가 확장 지원이 종료되었으며 이 설명서는 더 이상 업데이트되지 않습니다. 자세한 내용은 [기술 지원 기간](https://helpx.adobe.com/kr/support/programs/eol-matrix.html). 지원되는 버전 찾기 [여기](https://experienceleague.adobe.com/docs/).

## 개요 {#overview}

AEM Forms을 사용하면 적응형 양식을 초안으로 저장할 수 있습니다. 초안 기능은 사용자에게 진행 중인 양식을 유지 관리할 수 있는 옵션을 제공합니다. 그런 다음 사용자는 언제든지 장치에서 양식을 작성 및 제출할 수 있습니다.

기본적으로 AEM Forms은 초안 및 제출과 연관된 사용자 데이터를 의 게시 인스턴스에 저장합니다 `/content/forms/fp` 노드 아래에 있어야 합니다.

그러나 AEM Forms 포털 구성 요소는 초안 및 제출용 사용자 데이터 저장 구현을 사용자 정의할 수 있도록 해주는 데이터 서비스를 제공합니다. 예를 들어 조직에서 현재 구현한 데이터 저장소에 데이터를 저장할 수 있습니다.

사용자 데이터 저장소를 사용자 지정하려면 를 구현해야 합니다 [초안 데이터](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) 및 [제출 데이터](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p) 서비스.

## 사전 요구 사항 {#prerequisites}

* 활성화 [Forms 포털 구성 요소](/help/forms/using/enabling-forms-portal-components.md)
* 만들기 [forms 포털 페이지](/help/forms/using/creating-form-portal-page.md)
* 활성화 [forms 포털용 적응형 양식](/help/forms/using/draft-submission-component.md)
* 학습 [사용자 지정 스토리지 구현 세부 정보](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## 초안 데이터 서비스 {#draft-data-service}

사용자 초안 데이터의 저장소를 사용자 지정하려면 `DraftAFDataService` 인터페이스.

메서드 및 해당 인수에 대한 설명은 인터페이스의 다음 코드 샘플에 제공됩니다.

```java
public interface DraftAFDataService {
 
 /**
  * Deletes the user data stored against the ID passed as the argument
  * 
  * @param draftDataID
  * @return status for the just occurred delete draft UserData operation 
  * @throws FormsPortalException
  */
 public Boolean deleteAFDraftUserData (String draftDataID) throws FormsPortalException;
 
 /**
  * Saves user data provided in the argument map
  * 
  * @param draftUserDataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID") in case of update
  * @return userData ID would be returned which needs to be saved in metadata node 
  * @throws FormsPortalException
  */
 public String saveAFUserData (Map<String, Object> draftUserDataMap) throws FormsPortalException;
 
 /**
  * Gets the user data stored against the ID passed as the argument
  * 
  * @param Draft DataID
  * @return guideState (which would then be populated in adaptive form to reload the draft) which is stored against draftDataID
  * @throws FormsPortalException
  */
 public byte[] getAFDraftUserData(String draftDataID) throws FormsPortalException;
 
 /**
  * Saves the attachments for current adaptive form instance 
  * 
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later)
  * @throws FormsPortalException
  */
 public String saveAttachments(byte[] attachmentBytes) throws FormsPortalException;
}
```

## 데이터 서비스 제출 {#submission-data-service}

사용자 제출 데이터 저장소를 사용자 지정하려면 의 모든 방법에 대한 구현을 제공해야 합니다 `SubmittedAFDataService` 인터페이스.

메서드 및 해당 인수에 대한 설명은 인터페이스의 다음 코드 샘플에 제공됩니다.

```java
public interface SubmittedAFDataService {
 
 /**
  * Submits the user data passed in argument map
  * 
  * @param submittedAFUserdataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID")
  * @return userData ID is returned that needs to be saved in the metadata node
  * @throws FormsPortalException
  */
 public String submitAFUserData (Map<String, Object> submittedAFUserdataMap) throws FormsPortalException;
 
 /**
  * Gets the user data stored against the ID passed as argument
  * 
  * @param submitDataID
  * @return guideState which would be used to open DOR
  * @throws FormsPortalException
  */
 public byte[] getSubmittedAFUSerData(String submitDataID) throws FormsPortalException;
 
 /**
  * Deletes user data stored against the ID passed as argument
  * 
  * @param Submit DataID
  * @return status of the delete operation on Submitted User data
  * @throws FormsPortalException
  */
 
 public Boolean deleteSubmittedAFUserData(String submitDataID) throws FormsPortalException;
 
 /**
  * Submits the attachment bytes passed as argument
  * 
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later) 
  * @throws FormsPortalException
  */
 public String submitAttachments(Object attachmentBytes) throws FormsPortalException;

}
```
