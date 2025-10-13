# Dockerfile

# 1. 기반 이미지: NVIDIA 공식 Isaac Sim 이미지를 사용합니다.
FROM nvcr.io/nvidia/isaac-sim:5.0.0

# 2. (선택사항) 나만의 에셋이나 파일을 이미지에 추가합니다.
# 예시: 내 컴퓨터의 'my_robot_assets' 폴더를 이미지 안으로 복사
# COPY ./my_robot_assets /workspace/assets

# 3. (선택사항) 추가 라이브러리를 설치합니다.
# 예시: Isaac Sim 내부의 python으로 pandas 설치
# RUN /isaac-sim/python.sh -m pip install pandas

# 4. EULA 동의와 같은 기본적인 환경변수만 설정합니다.
# (Nucleus 서버 정보 등은 ApplicationProfile에서 주입하는 것이 더 유연합니다.)
ENV ACCEPT_EULA="Y"
ENV PRIVACY_CONSENT="Y"
