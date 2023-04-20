# TIMP-lab04

1) git clone https://github.com/TujhFoxnime/TIMP-lab03.git
2) cd TIMP-lab03
3) git remote remove origin удаляем связь с репозиторием лаб03
4) git remote add origin https://github.com/TujhFoxnime/TIMP-lab04.git привязка к новому репозиторию
5) mkdir .github
6) cd .github
7) mkdir workflows
8) cd workflows
9) 
* name: CMake     (имя процесса)

* on:                      (триггеры - условия для запуска процесса)
*  push:
*   branches: [main]
*  pull_request:
*   branches: [main]
* 
* jobs:                    (список задач)
*  build_Linux:                (название задачи)
* 
*   runs-on: ubuntu-latest          (ос запуска задачи)
* 
*   steps:                          (шаги задачи)
*   - uses: actions/checkout@v3        (поддержка Git_Actions)
* 
*   - name: Configure Solver                    (Настройка)
*     run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build   (на этой переменной хранится путь до рабочей директории)
* 
*   - name: Build Solver                        (Постройка)
*     run: cmake --build ${{github.workspace}}/solver_application/build
* 
*   - name: Configure HelloWorld
*     run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build
* 
*   - name: Build HelloWorld
*     run: cmake --build ${{github.workspace}}/hello_world_application/build

10) cd /name_lab_03/
11) git add .github
12) git commit -m "added CI.yml"
13) git push origin main
