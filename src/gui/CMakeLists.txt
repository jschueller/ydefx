# Copyright (C) 2019  EDF R&D
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307 USA
#
# See http://www.salome-platform.org/ or email : webmaster.salome@opencascade.com
#

#INCLUDE(UseQtExt)
#INCLUDE_DIRECTORIES(
#  ${QT_INCLUDES}
#  ${PROJECT_SOURCE_DIR}/src/cpp
#)

#ADD_DEFINITIONS(
#  ${QT_DEFINITIONS}
#  ${GUI_DEFINITIONS}
#  ${PYTHON_DEFINITIONS}
#)
SET(CMAKE_AUTOMOC ON)

INCLUDE_DIRECTORIES(
  ${PROJECT_SOURCE_DIR}/src/cpp
  ${PYTHON_INCLUDE_DIR}
)

ADD_DEFINITIONS(
  ${PYTHON_DEFINITIONS}
)

SET(YDEFX_SOURCES
  ResourceWidget.cxx
  ParamsConfig.cxx
  PathsConfig.cxx
  QuickConfig.cxx
)

SET(YDEFX_HEADERS
  ResourceWidget.hxx
)

SET(YDEFX_link_LIBRARIES
  Qt5::Widgets
  ydefx
)

ADD_LIBRARY(ydefxgui ${YDEFX_SOURCES})
TARGET_LINK_LIBRARIES(ydefxgui ${YDEFX_link_LIBRARIES})
TARGET_INCLUDE_DIRECTORIES(ydefxgui PUBLIC
                          $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/gui>
                          $<INSTALL_INTERFACE:include>)

ADD_EXECUTABLE(ydefxgui.exe ydefxgui.cxx)
TARGET_LINK_LIBRARIES(ydefxgui.exe ydefxgui)