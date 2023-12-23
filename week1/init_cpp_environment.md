# C++ 환경 셋팅

#### [MacOS](https://headf1rst.github.io/c++/clang-c++17/)

## 1. 컴파일러 설치


### Ubuntu & MacOS
```bash
sudo apt-get install g++

brew install clang
```

### Windows
[# PS를 위한 VSCode C++ 셋팅하기](https://velog.io/@phantom5087/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98CVSCode-PS%EB%A5%BC-%EC%9C%84%ED%95%9C-VSCode-C-%EC%85%8B%ED%8C%85%ED%95%98%EA%B8%B0)

1. [Install mingw](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/](https://sourceforge.net/projects/mingw-w64/files/mingw-w64/)

2. 환경변수 지정
![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/99bbd8a1-511c-4be0-bdaa-38584c8f1313)

**고급 ->환경변수 -> path -> 편집 -> mingw의 bin폴더 파일 경로**
![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/73282efa-4ee2-4475-b4e2-d1e855a770e4)



## 2. Visual Studio Code 설치
![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/57016b6d-ec73-4a2e-a40d-4714aff916af)

[Download](https://code.visualstudio.com/download)



## 3. Visual Studio Code C++ 확장 프로그램 설치

![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/6046438a-930a-42d1-91f5-42b502b2db9a)


## 4. 확장 프로그램 컴파일러 경로 연동

VSCode 내에서 control + shift + p 눌러서 시스템 메뉴 검색 열기

![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/09c5f50f-7218-4a5e-b453-91c3a252fe25)


![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/7815119a-9f43-48ba-b911-6c3283402474)


## 5. 컴파일러 단축키 연동

![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/ff8c98fc-b4bc-4727-8254-43c0a9dd9a8a)


아래 내용 저장
```json
{
    "version": "2.0.0",
    "runner": "terminal",
    "type": "shell",
    "echoCommand": true,
    "presentation" : { "reveal": "always" },
    "tasks": [
          //C++ 컴파일
          {
            "label": "save and compile for C++",
            "command": "g++",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "group": "build",

            //컴파일시 에러를 편집기에 반영
            //참고:   https://code.visualstudio.com/docs/editor/tasks#_defining-a-problem-matcher

            "problemMatcher": {
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}"
                ],
                "pattern": {
                    // The regular expression.
                  //Example to match: helloWorld.c:5:3: warning: implicit declaration of function 'prinft'
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        },
        //C 컴파일
        {
            "label": "save and compile for C",
            "command": "gcc",
            "args": [
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "group": "build",

            //컴파일시 에러를 편집기에 반영
            //참고:   https://code.visualstudio.com/docs/editor/tasks#_defining-a-problem-matcher

            "problemMatcher": {
                "fileLocation": [
                    "relative",
                    "${workspaceRoot}"
                ],
                "pattern": {
                    // The regular expression.
                  //Example to match: helloWorld.c:5:3: warning: implicit declaration of function 'prinft'
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            }
        },
        // 바이너리 실행(Ubuntu)
        // {
        //     "label": "execute",
        //     "command": "${fileDirname}/${fileBasenameNoExtension}",
        //     "group": "test"
        // }
        // 바이너리 실행(Windows)
        {
            "label": "execute",
            "command": "cmd",
            "group": "test",
            "args": [
                "/C", "${fileDirname}\\${fileBasenameNoExtension}"
            ]
   
        }
    ]
}
```

단축키 지정

![image](https://github.com/divisonofficer/cpp_and_algorithm/assets/41609506/532ef969-a8fb-43a0-bfef-e330a48e1be5)

```json
[  
//컴파일  
{ "key": "ctrl+alt+c", "command": "workbench.action.tasks.build" },  
//실행  
{ "key": "ctrl+alt+r", "command": "workbench.action.tasks.test" }  
]
```


