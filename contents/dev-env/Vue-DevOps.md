# DevOps 개발 환경 구축

> 🚩 GitHub을 활용해 로컬 프로젝트를 배포합니다.
>
> 1. Vue cli를 통한 프로젝트 생성
> 2. GitHub Pages에 직접 빌드한 프로젝트를 올려 수동 배포
> 3. GitHub Actions를 통한 배포 자동화
>
> 👉 [구현 코드 보러가기](https://github.com/Xxell-8/vue-devops)



## 🔥 Today I Learned

#### 1. DevOps

- `Development` +  `Operations`
- 애플리케이션과 서비스를 빠른 속도로 제공할 수 있도록 조직의 역량을 향상시키는 문화 철학, 방식 및 도구의 조합입니다.
  - 개발 팀(Dev)와 IT 운영 팀(Ops) 간의 원활하고 지속적인 커뮤니케이션과 협업을 장려하여, SW 기획부터 개발, 테스트, 배포, 운영 등 모든 DevOps 라이프사이클 단계에서 긴밀한 관계가 유지될 수 있도록 합니다.



#### 2. NPM 커스텀 명령어

- npm 커스텀 명령어란, 사용자가 임의로 명령어의 이름과 동작을 정의해서 사용할 수 있는 기능입니다.

  - npm의 패키지 관리 파일인 `package.json`에서 `scripts`라는 속성을 통해 커스텀 명령어를 지정할 수 있습니다.

- [활용] GitHun Pages로 배포하기 위해 [gh-pages](https://www.npmjs.com/package/gh-pages)를 추가한 뒤,

  - package.json에서 배포에 필요한 명령어를 추가합니다.

  ```json
  "scripts": {
      "serve": "vue-cli-service serve",
      "build": "vue-cli-service build",
      "predeploy": "vue-cli-service build",
      "deploy": "gh-pages -d dist",
      "clean": "gh-pages-clean",
      "test:unit": "vue-cli-service test:unit",
      "lint": "vue-cli-service lint"
    },
  ```

  cf.  `gh-pages`는 GitHub repo에 **브랜치를 생성**하여, 배포를 위해 빌드한 프로젝트를 올립니다.



#### 3. GitHub Actions

- GitHub Actions는 GitHub의 SW 개발 workflow에서 작업을 자동화하기 위한 패키지 스크립트입니다.

  - 새로운 소스 코드 Push 혹은 PR 이벤트 등에 반응하여 트리거하도록 구성할 수 있으며,
  - 이를 통해 빠르고 안정적인 배포 및 운영이 가능한 DevOps 환경을 구축할 수 있습니다.

- [활용] Simple Workflow 파일(`deploy.yml`)을 작성하여, 

  - Vue로 작성된 소스 코드를 자동으로 **테스트**한 뒤 **빌드**하여 GitHub Pages에 **배포**하는 작업을 **자동화**할 수 있습니다.

  - 배포 스크립트인 workflow 파일에 자동화할 작업을 추가합니다.

    ```yaml
    jobs:
      deploy:
        runs-on: ubuntu-latest
    
        steps:
          - name: Checkout source code
            uses: actions/checkout@master
    
          - name: Set up Node.js
            uses: actions/setup-node@master
            with:
              node-version: 14.x
          
          - name: Install dependencies
            run: npm install
          
          - name: Test unit
            run: npm run test:unit
          
          - name: Build Page
            run: npm run build
            env:
              NODE_ENV: production
    
          - name: Deploy to gh-pages
            uses: peaceiris/actions-gh-pages@v3
            with:
              github_token: ${{ secrets.GITHUB_TOKEN }}
              publish_dir: ./dist
    ```



