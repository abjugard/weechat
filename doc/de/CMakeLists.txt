#
# Copyright (C) 2003-2017 Sébastien Helleu <flashcode@flashtux.org>
#
# This file is part of WeeChat, the extensible chat client.
#
# WeeChat is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# WeeChat is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with WeeChat.  If not, see <http://www.gnu.org/licenses/>.
#

if(ENABLE_MAN)
  # man page
  add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/weechat.1
    COMMAND ${ASCIIDOCTOR_EXECUTABLE} ARGS ${ASCIIDOCTOR_ARGS} -b manpage -o weechat.1 ${CMAKE_CURRENT_SOURCE_DIR}/weechat.1.de.adoc
    DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/weechat.1.de.adoc
    ${CMAKE_CURRENT_SOURCE_DIR}/cmdline_options.de.adoc
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Building weechat.1 (de)"
  )
  add_custom_target(doc-man-de ALL DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/weechat.1)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/weechat.1 DESTINATION ${MANDIR}/de/man1)
endif()

if(ENABLE_DOC)

  # user's guide
  add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/weechat_user.de.html
    COMMAND ${ASCIIDOCTOR_EXECUTABLE} ARGS ${ASCIIDOCTOR_ARGS} -o weechat_user.de.html ${CMAKE_CURRENT_SOURCE_DIR}/weechat_user.de.adoc
    DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/../docinfo.html
    ${CMAKE_CURRENT_SOURCE_DIR}/weechat_user.de.adoc
    ${CMAKE_CURRENT_SOURCE_DIR}/cmdline_options.de.adoc
    ${CMAKE_CURRENT_SOURCE_DIR}/autogen/user/*.adoc
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Building weechat_user.de.html"
  )
  add_custom_target(doc-user-de ALL DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/weechat_user.de.html)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/weechat_user.de.html DESTINATION ${SHAREDIR}/doc/${PROJECT_NAME})

  # scripting guide
  add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/weechat_scripting.de.html
    COMMAND ${ASCIIDOCTOR_EXECUTABLE} ARGS ${ASCIIDOCTOR_ARGS} -o weechat_scripting.de.html ${CMAKE_CURRENT_SOURCE_DIR}/weechat_scripting.de.adoc
    DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/../docinfo.html
    ${CMAKE_CURRENT_SOURCE_DIR}/weechat_scripting.de.adoc
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Building weechat_scripting.de.html"
  )
  add_custom_target(doc-scripting-de ALL DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/weechat_scripting.de.html)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/weechat_scripting.de.html DESTINATION ${SHAREDIR}/doc/${PROJECT_NAME})

  # FAQ
  add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/weechat_faq.de.html
    COMMAND ${ASCIIDOCTOR_EXECUTABLE} ARGS ${ASCIIDOCTOR_ARGS} -o weechat_faq.de.html ${CMAKE_CURRENT_SOURCE_DIR}/weechat_faq.de.adoc
    DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/../docinfo.html
    ${CMAKE_CURRENT_SOURCE_DIR}/weechat_faq.de.adoc
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Building weechat_faq.de.html"
  )
  add_custom_target(doc-faq-de ALL DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/weechat_faq.de.html)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/weechat_faq.de.html DESTINATION ${SHAREDIR}/doc/${PROJECT_NAME})

  # quickstart
  add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/weechat_quickstart.de.html
    COMMAND ${ASCIIDOCTOR_EXECUTABLE} ARGS ${ASCIIDOCTOR_ARGS} -o weechat_quickstart.de.html ${CMAKE_CURRENT_SOURCE_DIR}/weechat_quickstart.de.adoc
    DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/../docinfo.html
    ${CMAKE_CURRENT_SOURCE_DIR}/weechat_quickstart.de.adoc
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Building weechat_quickstart.de.html"
  )
  add_custom_target(doc-quickstart-de ALL DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/weechat_quickstart.de.html)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/weechat_quickstart.de.html DESTINATION ${SHAREDIR}/doc/${PROJECT_NAME})

  # tester's guide
  add_custom_command(
    OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/weechat_tester.de.html
    COMMAND ${ASCIIDOCTOR_EXECUTABLE} ARGS ${ASCIIDOCTOR_ARGS} -o weechat_tester.de.html ${CMAKE_CURRENT_SOURCE_DIR}/weechat_tester.de.adoc
    DEPENDS
    ${CMAKE_CURRENT_SOURCE_DIR}/../docinfo.html
    ${CMAKE_CURRENT_SOURCE_DIR}/weechat_tester.de.adoc
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Building weechat_tester.de.html"
  )
  add_custom_target(doc-tester-de ALL DEPENDS ${CMAKE_CURRENT_BINARY_DIR}/weechat_tester.de.html)
  install(FILES ${CMAKE_CURRENT_BINARY_DIR}/weechat_tester.de.html DESTINATION ${SHAREDIR}/doc/${PROJECT_NAME})

endif()
