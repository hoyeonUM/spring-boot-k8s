##### 로컬(window) 에서 k8s 로 spring-boot web-service 실행하기
1. docker for window 설치
https://www.docker.com/get-started
2. kubernetes 활성화
docker for window -> setting -> Enable Kubernetes 설정
3. git pull https://github.com/hoyeonUM/spring-boot-k8s.git
4. cd <work space>
5. deployment / service 설정
kubectl apply -f .\kubernetes\deployment.yaml
kubectl apply -f .\kubernetes\service.yaml
6. 엔드포인트 확인
kubectl get service spring-boot-service -o wide


##### 도커파일 만들기
1. cd <work space>
2. docker build ./ -t dus815/spring-boot-demo:<version>
3. docker push dus815/spring-boot-demo:<version>

##### kubernates 대시보드 만들기
1. cd <work space>
2. 대시보드 설정
kubectl create -f .\kubernetes\dashboard.yaml
3. 프록시 설정
kubectl proxy
4. 토큰 조회
kubectl -n kubernetes-dashboard describe secret
5. 대시보드 접속
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/.

##### 참고문서
1. eksworkshop
https://awskrug.github.io/eks-workshop/deploy/deploynodejs/
2. 스프링부트 시작하기
https://www.jetbrains.com/help/idea/your-first-spring-application.html
3. 도커이미지 만들기
https://inma.tistory.com/148
4. 쿠버네티스 dashboard
https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/