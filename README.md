# cv_bridge 

This repos is a smallest [cv_bridge](https://github.com/ros-perception/vision_opencv) package used only with c++.

# Use as submodule 
1. add to you repos 
```shell
git submodule add https://github.com/Sologala/cv_bridge.git
```
2. useed as a cmake subdirectory

```
add_subdirectory(cv_bridge)
```

```
target_link_libraries(
   ${PROJECT_NAME}
   cv_bridge
)
```

