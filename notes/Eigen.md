Using VSCode to develop C/C++ programs 3 profiles:
1. tasks.json: Compiler constructuon profiles.
2. launch.json: Debugger settings profiles.
3. c_cpp_properties_json: Compiler paths and smart code tips profiles.


For intellisense to work in vscode for Eigen edit c_cpp_properties.json:
ctrl+shit+p, open c/c++:Edit configurations (JSON), add
```
"includePath": [
	"${workspaceFolder}/**",
	"/usr/include/eigen3" // Eigen
]
```
Check if Eigen library is configured successfully:
```
#include <Eigen/Core>
#include <Eigen/Dense>

```

