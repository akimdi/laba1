cmake_minimum_required(VERSION 3.3)

project(Laba_1)

set(SOURCES Program.cpp ../source/DerivedCars/BMW.cpp 
                        ../source/DerivedCars/VAZ2115.cpp 
                        ../source/Facade/Cars.cpp 
                        ../source/ICar/ICar.cpp 
                        ../source/State/IState.cpp)

set(HEADERS ../source/DerivedCars/BMW.h 
                        ../source/DerivedCars/VAZ2115.h 
                        ../source/Facade/Cars.h 
                        ../source/ICar/ICar.h 
                        ../source/State/IState.h)

add_library(AiPPS STATIC ${SOURCES} ${HEADERS})

include_directories(../source/DerivedCars Facade ICar State lib)

find_library(APRUTIL NAMES "vld" PATHS ${PROJECT_SOURCE_DIR}/lib)

add_library(vldlib SHARED ${APRUTIL})

SET_TARGET_PROPERTIES(vldlib PROPERTIES LINKER_LANGUAGE C++)

add_executable(laba_1 ${SOURCES} ${HEADERS})

target_link_libraries(laba_1 AiPPS)