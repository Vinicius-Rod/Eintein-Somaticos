# Eintein-Somaticos
Exercício de Somáticos

# Instalar softwares
SRATOOLKIT BWA SAMTOOLS
``` bash
brew install sratoolkit bwa samtools
```
```bash
pip install parallel-fastq-dump
```
```bash
wget -c https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/3.0.0/sratoolkit.3.0.0-ubuntu64.tar.gz
```
```bash
tar -zxvf sratoolkit.3.0.0-ubuntu64.tar.gz
```
```bash
export PATH=$PATH://workspace/somaticoEP2/sratoolkit.3.0.0-ubuntu64/bin/
```

## Instalar GATK
```bash
wget -c https://github.com/broadinstitute/gatk/releases/download/4.2.2.0/gatk-4.2.2.0.zip
```
```bash
unzip gatk-4.2.2.0.zip
```

##Baixar arquivos
```bash
time parallel-fastq-dump --sra-id SRR8856724 \
--threads 10 \
--outdir ./ \
--split-files \
--gzip
```
