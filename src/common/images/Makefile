# SPDX-License-Identifier: BSD-2-Clause

# Copyright (C) 2026 embedded brains GmbH & Co. KG

all: traceability.pdf

%.eps: %.dot
	dot -Teps $^ -o$@

%.pdf: %.dot
	dot -Tpdf $^ -o$@
