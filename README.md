# Proxima File Upload Server

Http로 대용량 파일을 업로드 하기 위한 서버


## 업로드 서버 구축 방법

준비사항 : node.js 8.11.3이상이 설치되어 있어야 한다.

1. `git clone ssh://git@geminisoft.iptime.org/site-2018/huimai/file-upload-server.git`
2. `cd file-upload-server`
3. `yarn install 또는 npm install`
4. .env.example 파일을 .env파일로 복사 후 UPLOAD_PATH, SERVICE_PORT항목을 실환경에 맞게 변경
5. `yarn start 또는 npm start`

## 운영을 위한 주요 스크립트

업로드 서버는 pm2([http://pm2.keymetrics.io](http://pm2.keymetrics.io))를 사용하여 운영되며 주요 명령어는 package.json의 script에 미리 지정해 놓았음.

> yarn start 또는 npm start : 서비스를 시작한다.

> yarn stop 또는 npm stop : 서비스를 중지한다.

> yarn restart 또는 npm restart : 서비스를 재시작한다.

> yarn ps 또는 npm ps : 서비스 리스트를 조회한다.

> yarn logs 또는 npm logs : 서비스 로그를 조회한다.

### PM2 참고자료
- Node.js 의 프로세스 관리자인 PM2 모듈 사용하기([https://massivcode.com/5](https://massivcode.com/5))

## API Endpoint

POST /upload

- 업로드 할 경로
- 파일은 업로드 될 때 원본파일명-유니크아이디

GET /

- 업로드 테스트 페이지

## 업로드 서버 리턴 형식

```
{
    success: true, // true or false
    data: {
        org_filename: orgFilename.mp4, // original file name
        new_filename: newFilename.mp4  // new file name
    }
}
```
