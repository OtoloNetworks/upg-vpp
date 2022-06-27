# Copyright (c) 2020 Cisco and/or its affiliates.
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at:
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

vpp_find_path(HYPERSCAN_INCLUDE_DIR NAMES hs/hs.h)

if (NOT HYPERSCAN_INCLUDE_DIR)
  message(WARNING "-- hyperscan headers not found - upf plugin disabled")
  return()
endif()

vpp_plugin_find_library(upf HYPERSCAN_LIB hs)
include_directories(${HYPERSCAN_INCLUDE_DIR})

add_vpp_plugin(upf
  SOURCES
  upf.c
  upf_api.c
  upf_cli.c
  upf_gtpu_encap.c
  upf_gtpu_decap.c
  upf_flow_node.c
  upf_classify.c
  upf_adf.c
  upf_input.c
  upf_forward.c
  upf_session_dpo.c
  pfcp.c
  upf_pfcp.c
  upf_pfcp_api.c
  upf_pfcp_server.c
  upf_pfcp_session_server.c
  upf_proxy_accept.c
  upf_proxy_input.c
  upf_proxy_output.c
  upf_tcp_forward.c
  upf_proxy.c
  upf_app_db.c
  upf_ipfilter.c
  upf_app_dpo.c
  upf_ipfix.c
  upf_ipfix_templates.c
  flowtable_init.c
  flowtable.c
  unittest.c

  upf_gtpu_encap.c
  upf_gtpu_decap.c
  upf_flow_node.c
  upf_classify.c
  upf_proxy_accept.c
  upf_proxy_input.c
  upf_proxy_output.c
  upf_tcp_forward.c
  upf_input.c
  upf_forward.c
  upf_session_dpo.c

  API_FILES
  upf.api

  LINK_LIBRARIES
  ${HYPERSCAN_LIB}
)
