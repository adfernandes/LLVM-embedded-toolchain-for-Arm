#
# Copyright (c) 2020-2023, Arm Limited and affiliates.
# SPDX-License-Identifier: Apache-2.0
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

include ../../Makefile.conf

build: hello.elf

hello.elf: *.c
	$(BIN_PATH)/clang $(MICROBIT_TARGET) -g -T ../../ldscripts/microbit.ld -o hello.elf $^

%.hex: %.elf
	$(BIN_PATH)/llvm-objcopy -O ihex $< $@

run: hello.hex
	qemu-system-arm -M microbit -nographic -device loader,file=$<

debug: hello.hex
	qemu-system-arm -M microbit -nographic -device loader,file=$< -s -S

clean:
	rm -f *.elf *.hex

.PHONY: clean run debug
