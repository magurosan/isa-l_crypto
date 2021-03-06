########################################################################
#  Copyright(c) 2011-2016 Intel Corporation All rights reserved.
#
#  Redistribution and use in source and binary forms, with or without
#  modification, are permitted provided that the following conditions 
#  are met:
#    * Redistributions of source code must retain the above copyright
#      notice, this list of conditions and the following disclaimer.
#    * Redistributions in binary form must reproduce the above copyright
#      notice, this list of conditions and the following disclaimer in
#      the documentation and/or other materials provided with the
#      distribution.
#    * Neither the name of Intel Corporation nor the names of its
#      contributors may be used to endorse or promote products derived
#      from this software without specific prior written permission.
#
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#  "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
#  LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
#  A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
#  OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
#  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
#  LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
#  DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
#  THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
#  (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
#  OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
########################################################################

# Assembling AES requires including cbc_common.asm, gcm_defines.asm
src_include += -I $(srcdir)/aes

extern_hdrs += include/aes_gcm.h include/aes_cbc.h include/aes_xts.h include/aes_keyexp.h

lsrc     += aes/gcm_multibinary.asm aes/gcm_pre.c
lsrc     += aes/gcm128_avx_gen2.asm aes/gcm128_avx_gen4.asm aes/gcm128_sse.asm
lsrc     += aes/gcm256_avx_gen2.asm aes/gcm256_avx_gen4.asm aes/gcm256_sse.asm
lsrc     += aes/keyexp_multibinary.asm
lsrc     += aes/keyexp_128.asm aes/keyexp_192.asm aes/keyexp_256.asm
lsrc     += aes/cbc_multibinary.asm
lsrc     += aes/cbc_dec_128_x4_sse.asm aes/cbc_dec_128_x8_avx.asm
lsrc     += aes/cbc_dec_192_x4_sse.asm aes/cbc_dec_192_x8_avx.asm
lsrc     += aes/cbc_dec_256_x4_sse.asm aes/cbc_dec_256_x8_avx.asm
lsrc     += aes/cbc_enc_128_x4_sb.asm aes/cbc_enc_128_x8_sb.asm
lsrc     += aes/cbc_enc_192_x4_sb.asm aes/cbc_enc_192_x8_sb.asm
lsrc     += aes/cbc_enc_256_x4_sb.asm aes/cbc_enc_256_x8_sb.asm
lsrc     += aes/cbc_pre.c
lsrc     += aes/xts_aes_128_multibinary.asm
lsrc     += aes/XTS_AES_128_dec_sse.asm aes/XTS_AES_128_dec_expanded_key_sse.asm
lsrc     += aes/XTS_AES_128_enc_sse.asm aes/XTS_AES_128_enc_expanded_key_sse.asm
lsrc     += aes/XTS_AES_128_dec_avx.asm aes/XTS_AES_128_dec_expanded_key_avx.asm
lsrc     += aes/XTS_AES_128_enc_avx.asm aes/XTS_AES_128_enc_expanded_key_avx.asm
lsrc     += aes/xts_aes_256_multibinary.asm
lsrc     += aes/XTS_AES_256_dec_avx.asm aes/XTS_AES_256_dec_expanded_key_avx.asm
lsrc     += aes/XTS_AES_256_enc_avx.asm aes/XTS_AES_256_enc_expanded_key_avx.asm
lsrc     += aes/XTS_AES_256_dec_sse.asm aes/XTS_AES_256_dec_expanded_key_sse.asm
lsrc     += aes/XTS_AES_256_enc_sse.asm aes/XTS_AES_256_enc_expanded_key_sse.asm

other_src   += include/multibinary.asm
other_src   += include/test.h include/types.h include/reg_sizes.asm
other_src   += aes/gcm_defines.asm
other_src   += aes/cbc_common.asm aes/cbc_std_vectors.h
other_src   += aes/gcm_vectors.h aes/ossl_helper.h
other_src   += aes/xts_128_vect.h
other_src   += aes/xts_256_vect.h

check_tests += aes/cbc_std_vectors_test
check_tests += aes/gcm_std_vectors_test
check_tests += aes/xts_128_test
check_tests += aes/xts_256_test
check_tests += aes/xts_128_expanded_key_test
check_tests += aes/xts_256_expanded_key_test

unit_tests  += aes/cbc_std_vectors_random_test
unit_tests  += aes/gcm_std_vectors_random_test
unit_tests  += aes/xts_128_rand aes/xts_128_rand_ossl_test
unit_tests  += aes/xts_256_rand aes/xts_256_rand_ossl_test

perf_tests  += aes/cbc_ossl_perf
perf_tests  += aes/gcm_ossl_perf
perf_tests  += aes/xts_128_enc_ossl_perf
perf_tests  += aes/xts_256_enc_ossl_perf
perf_tests  += aes/xts_128_enc_perf aes/xts_128_dec_perf aes/xts_128_dec_ossl_perf
perf_tests  += aes/xts_256_enc_perf aes/xts_256_dec_perf aes/xts_256_dec_ossl_perf


cbc_ossl_perf: LDLIBS += -lcrypto
aes_cbc_ossl_perf_LDFLAGS = -lcrypto
cbc_std_vectors_random_test: LDLIBS += -lcrypto
aes_cbc_std_vectors_random_test_LDFLAGS = -lcrypto
gcm_ossl_perf: LDLIBS += -lcrypto
aes_gcm_ossl_perf_LDFLAGS = -lcrypto
gcm_std_vectors_random_test: LDLIBS += -lcrypto
aes_gcm_std_vectors_random_test_LDFLAGS = -lcrypto
xts_128_enc_ossl_perf: LDLIBS += -lcrypto
aes_xts_128_enc_ossl_perf_LDFLAGS = -lcrypto
xts_128_dec_ossl_perf: LDLIBS +=  -lcrypto
aes_xts_128_dec_ossl_perf_LDFLAGS = -lcrypto
xts_128_rand_ossl_test: LDLIBS +=  -lcrypto
aes_xts_128_rand_ossl_test_LDFLAGS = -lcrypto
xts_256_enc_ossl_perf : LDLIBS += -lcrypto
aes_xts_256_enc_ossl_perf_LDFLAGS = -lcrypto
xts_256_dec_ossl_perf : LDLIBS += -lcrypto
aes_xts_256_dec_ossl_perf_LDFLAGS = -lcrypto
xts_256_rand_ossl_test: LDLIBS += -lcrypto
aes_xts_256_rand_ossl_test_LDFLAGS = -lcrypto
