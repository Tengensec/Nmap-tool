git clone https://github.com/Tengensec/Nmap-tool.git

#!/bin/bash
# -----------------------------------------------------------------------------
# MIT License
# 
# Copyright (c) 2025 Tengensec

# 
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# -----------------------------------------------------------------------------

# Renkler
RED='\033[0;31m'
GREEN='\033[0;32m'
CYAN='\033[0;36m'
YELLOW='\033[1;33m'
NC='\033[0m'

# Banner
echo -e "${CYAN}"
echo '███    ██ ███    ███  █████  ██████ '
echo '████   ██ ████  ████ ██   ██ ██   ██'
echo '██ ██  ██ ██ ████ ██ ███████ ██████ '
echo '██  ██ ██ ██  ██  ██ ██   ██ ██     '
echo '██   ████ ██      ██ ██   ██ ██     '
echo -e "${NC}"
echo -e "${YELLOW}           NMAP SCANNER TOOL${NC}"
echo -e "${GREEN}           by ULYON CYBER TEAM${NC}\n"

function menu() {
    echo -e "${CYAN}Tarama Seçenekleri:${NC}"
    echo " 1) Hızlı tarama                (nmap -T4 <hedef>)"
    echo " 2) Tüm portları tara           (nmap -p- <hedef>)"
    echo " 3) Servis ve versiyon tarama   (nmap -sV <hedef>)"
    echo " 4) OS tespiti                  (nmap -O <hedef>)"
    echo " 5) Agresif tarama              (nmap -A <hedef>)"
    echo " 6) TCP SYN taraması            (sudo nmap -sS <hedef>)"
    echo " 7) UDP taraması                (sudo nmap -sU <hedef>)"
    echo " 8) Ping taraması               (nmap -sn <hedef>)"
    echo " 9) Firewall tespiti            (nmap -sA <hedef>)"
    echo "10) Script taraması             (nmap -sC <hedef>)"
    echo ""
}

function run_scan() {
    echo -e "${YELLOW}[*] Tarama başlatılıyor...${NC}\n"
    case $1 in
        1) echo -e "${GREEN}[+] Hızlı tarama...${NC}"; nmap -T4 "$target";;
        2) echo -e "${GREEN}[+] Tüm portlar taranıyor...${NC}"; nmap -p- "$target";;
        3) echo -e "${GREEN}[+] Servis ve versiyon bilgisi...${NC}"; nmap -sV "$target";;
        4) echo -e "${GREEN}[+] OS tespiti...${NC}"; sudo nmap -O "$target";;
        5) echo -e "${GREEN}[+] Agresif tarama...${NC}"; nmap -A "$target";;
        6) echo -e "${GREEN}[+] TCP SYN taraması...${NC}"; sudo nmap -sS "$target";;
        7) echo -e "${GREEN}[+] UDP taraması...${NC}"; sudo nmap -sU "$target";;
        8) echo -e "${GREEN}[+] Ping sweep...${NC}"; nmap -sn "$target";;
        9) echo -e "${GREEN}[+] Firewall tespiti...${NC}"; nmap -sA "$target";;
        10) echo -e "${GREEN}[+] Script taraması...${NC}"; nmap -sC "$target";;
        *) echo -e "${RED}[!] Geçersiz seçim.${NC}";;
    esac
}

read -p "$(echo -e ${CYAN}[*] Hedef IP / Domain girin: ${NC})" target
echo ""
menu
read -p "$(echo -e ${YELLOW}[*] Bir seçenek girin (1-10): ${NC})" choice
echo ""
run_scan "$choice"
