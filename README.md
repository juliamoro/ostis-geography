## OSTIS-geography
OSTIS-geography is an open-source knowledge base for geographical system for Open Semantic Technology for Intelligent Systems. System includes OpenStreetMap support to display geographical objects. There is special agent that can display object on map according to their description.

## Install

Linux:
```sh
git clone https://github.com/Vikort/ostis-geography
git checkout pis
cd {project-name}/scripts
./install_ostis.sh
```

## Build knowledge base
Linux:
```sh
cd {project-name}/ostis-web-platform/scripts
./build_kb.sh
```

## Run
### Option 1. Run sctp-server & sc-web
Please note that JSON Websocket protocol will be available as well after start.
Run on Linux:
```sh
#Terminal 1
cd {project-name}/ostis-web-platform/scripts
./run_sc_server.sh
#Terminal 2
cd {project-name}/ostis-web-platform/scripts
./run_sc_web.sh
```

Then open localhost:8000 in your browser.
![](https://i.imgur.com/6SehI5s.png)

You can open localhost:8090 in your browser as well to see the new web interface version.

## OpenStreetMap
To check if everything is working run system, find minsk, switch to expert mode and change from scs view mode to OpenStreetMap.

## Pull requests
1. Add understandable title to the Pull Request which covers all changes in this Pull Request.

Good Example:
821701 Brunner KB schools

2. Also you can write this information inside Pull request, like here https://github.com/Vikort/ostis-geography/pull/3 or here https://github.com/Vikort/ostis-geography/pull/4
3. Dont forget about newline at the end of the file
4. Not necessary, but we will appreciate if you clean your commit history

## Project Structure

### kb
The place for the knowledge base of your app. Put your **.scs** files here.

### problem-solver
The place for the problem solver of your app. Put your agents here.

#### Agents on C++
Some tips:
- Store your modules with C++ agents in *problem-solver/cxx*;
- After updating your C++ code you need to rebuild problem-solver. Just run:  
```
cd {project-name}/scripts
./build_problem_solver.sh
```
For a full rebuild with the deleting of the *bin* and *build* folders run:
```
cd patient-care/scripts
./build_problem_solver.sh -f
```

- To enable debug:
    * add *SET(CMAKE_BUILD_TYPE Debug)* line 
    to *{project-name}/CMakeLists.txt* file;
    * rebuild problem-solver.
- You can see an example module with a C++ agent [here](problem-solver/cxx/exampleModule/README.md).

#### Agents on Python
Some tips:
- Store your modules with Python agents in *problem-solver/py*;
- After updating your Python code you don't need to rebuild problem-solver;
- You can see example modules using Python [here](problem-solver/py). 

### interface

The place for your interface modules.

To learn more about creating web components for the new web interface version please follow this [link](https://github.com/MikhailSadovsky/sc-machine/tree/example/web/client)

#### sc-web-extensions
The place for your extensions using **IMS interface(sc-web)** standard. 

*Your extensions are not applied to sc-web automatically for now, but you can do it by hand.*

### scripts
The place for scripts of your app.

#### build_problem_solver.sh [-f, --full]
Build the problem-solver of your app. Use an argument *-f* or *--full* for a complete rebuild of the problem-solver with the deleting of the *ostis-web-platform/sc-machine/bin* and *ostis-web-platform/sc-machine/build* folders.

#### install_ostis.sh
Install or update the OSTIS platform.

#### install_subsystems.sh
Building a problem solver and a knowledge base of subsystems.