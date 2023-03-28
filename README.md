# TIMP-lab04

git clone https://github.com/TujhFoxnime/TIMP-lab03.git
cd TIMP-lab03
git remote remove origin удаляем связь с репозиторием лаб03
git remote add origin https://github.com/TujhFoxnime/TIMP-lab04.git привязка к новому репозиторию
mkdir .github
cd .github
mkdir workflows
cd workflows
nano CI.ymlname: CMake имя процессаon: список триггеров (условия при котором запускается процесс)push:branches: [main]pull_request:branches: [main]jobs: список задачbuild_Linux: название задачиruns-on: ubuntu-latest на какой ос будет запущена задачаsteps: шаги задачиuses: actions/checkout@v3 поддержка гит-экшонсname: Configure Solver
run: cmake{{github.workspace}}/ на этой переменной хранится путь до рабочей директории на удал сервере гитаsolver_application/buildname: Build Solverrun: cmake --build ${{github.workspace}}/solver_application/build
name: Configure HelloWorldrun: cmake{{github.workspace}}/hello_world_application/buildname: Build HelloWorldrun: cmake --build ${{github.workspace}}/hello_world_application/buildbuild_Windows:runs-on: windows-lateststeps:uses: actions/checkout@v3name: Configure Solverrun: cmake{{github.workspace}} \solver_application/buildname: Build Solverrun: cmake --build ${{github.workspace}}/solver_application/buildname: Configure HelloWorldrun: cmake{{github.workspace}}/hello_world_application/buildname: Build HelloWorldrun: cmake --build ${{github.workspace}}/hello_world_application/buildctrl+O
enter ctrl+X
cd /name_lab_03/
git add .github
git commit -m "added CI.yml"
git push origin main
