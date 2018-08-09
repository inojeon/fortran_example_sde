# Makefile sample - SDE 형태의 1개 입력파일 읽기 Fortran 언어

EDISON 시뮬레이션 SW 개발자를 위한 1개의 SDE 입력 파일 읽어, 입력파일안에 있는 변수값을 출력하는 fortran언어 예제 파일입니다.

```
src/
 - Makeflie
 - main.f     //main 소스 코드
inp/
 - input.dat //샘플 입력 파일
```


입력 파일의 경우에는 변수와 값 구분자를 ' '을 사용하였으며, 변수와 변수 사이를 구분하기 위해 ' \n '를 사용하였습니다. 파일로 입력을 받으며, 샘플 입력 파일은 아래와 같으며, **inp** 폴더에 **input.dat** 로 저장되어 있습니다.

```
INT1 42
REAL1 42.112
LIST1 a
VECTOR1 [ 1 0 0 ]
```


본 예제는 ./[실행파일명] -[옵션] [입력 파일 경로]로 실행시 옵션 뒤에 입력된 경로의 파일을 열고 닫는 예제로 Makefile과 소스코드는  **src** 폴더에 저장되어 있으며, 컴파일이 완료되면 바이너리 파일은 **bin** 폴더에 저장됩니다.


## 설치하기

zip 파일을 다운로드 받아 압축을 풀거나 ```git clone``` 명령어를 이용하여, 프로젝트를 가져올 수 있습니다.

```
$ git clone https://github.com/sp-edison/c_example_gnuplot.git
```

다운로드가 완료되면, ```fortran_example_sde``` 폴더가 생성되며, **src** 폴더로 이동하여 **make all** 명령어를 사용하면, 컴파일이 완료됩니다.

```
$ cd fortran_example_onedsde/src
$ make all
gfortran -c main.f -o main.o
Compiled main.f successfully!
fortran -o ../bin/Hollo.x main.o
Linking complete!
```

기본 값으로 등록된 TARGET 값이 Sde.x이며, 생성된 bin 폴더로 이동하여, 아래와 같이 명령어를 입력하면 실행이 됩니다.

```
$ cd ../bin
$ ./Sde.x -i ../inp/input.dat
 ../inp/input.dat
 Input file path : ../inp/input.dat
 INT1 =           42
 REAL1 =    42.112000000000002
 list = a
 Vector =            1           0           0
 Inputdeck file read end
```

> 해당 예제를 이용하여 EDISON 웹포털에서 자동으로 소스 컴파일을 하실수 있습니다. 자동으로 소스 컴파일을 하기위해 선행되야하는 조건은 아래와 같습니다.
> - 본 예제와 같이 Makefile과 소스코드는 **src** 폴더에 저장되어 있어야 합니다. 
> - **src** 폴더 안에서 ```make all``` 커맨드 입력시, 컴파일이 정상적으로 왼료된 경우 바이너리 파일이 **bin** 폴더에 저장이 되면 됩니다.
> - 바이너리가 실행되는 과정에서 $PATH, $LD_LIBRARY_PATH 등의 환경변수 등록이 필요한경우**bin** 폴더 안에 **simrc**라는 파일을 만들어 해당 변수들을 추가해야 합니다. 
> - 결과 파일은 실행 파일이 있는 경로에 result 폴더를 생성해야 합니다.

```fortran
      CALL SYSTEM("rm -rf result")
      CALL SYSTEM("mkdir result")
```
