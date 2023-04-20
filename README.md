# TIMP-lab04

1) git clone https://github.com/TujhFoxnime/TIMP-lab03.git
2) cd TIMP-lab03
3) git remote remove origin удаляем связь с репозиторием лаб03
4) git remote add origin https://github.com/TujhFoxnime/TIMP-lab04.git привязка к новому репозиторию
5) mkdir .github
6) cd .github
7) mkdir workflows
8) cd workflows
9) nano CI.ymlname: CMake имя процесса
on: список триггеров (условия при котором запускается процесс)
push:
branches: [main]
pull_request:
branches: [main]
jobs: список задачbuild_Linux: название задачиruns-on: ubuntu-latest на какой ос будет запущена задачаsteps: шаги задачиuses: actions/checkout@v3 поддержка гит-экшонсname: Configure Solver
run: cmake{{github.workspace}}/ на этой переменной хранится путь до рабочей директории на удал сервере гитаsolver_application/buildname: Build Solverrun: cmake --build ${{github.workspace}}/solver_application/build
name: Configure HelloWorldrun: cmake{{github.workspace}}/hello_world_application/buildname: Build HelloWorldrun: cmake --build ${{github.workspace}}/hello_world_application/buildbuild_Windows:runs-on: windows-lateststeps:uses: actions/checkout@v3name: Configure Solverrun: cmake{{github.workspace}} \solver_application/buildname: Build Solverrun: cmake --build ${{github.workspace}}/solver_application/buildname: Configure HelloWorldrun: cmake{{github.workspace}}/hello_world_application/buildname: Build HelloWorldrun: cmake --build ${{github.workspace}}/hello_world_application/buildctrl+O
10) cd /name_lab_03/
11) git add .github
12) git commit -m "added CI.yml"
13) git push origin main
