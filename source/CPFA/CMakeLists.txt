
###############################################
# define shared object files
###############################################

add_library(CPFA_loop_functions     SHARED      CPFA_loop_functions.h
                                                CPFA_loop_functions.cpp
                                                CPFA_qt_user_functions.h
                                                CPFA_qt_user_functions.cpp)

add_library(CPFA_controller         SHARED      CPFA_controller.h
                                                CPFA_controller.cpp
                                                CPFA_loop_functions.h
                                                CPFA_loop_functions.cpp)
###############################################
# link shared object files to dependencies
###############################################

target_link_libraries(  CPFA_controller
                        BaseController
                        Pheromone)

target_link_libraries(  CPFA_loop_functions
                        CPFA_controller
                        argos3core_simulator
                        argos3plugin_simulator_entities
                        argos3plugin_simulator_footbot
                        argos3plugin_simulator_genericrobot
                        argos3plugin_simulator_qtopengl
                        ${ARGOS_QTOPENGL_LIBRARIES})
