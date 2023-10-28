# Eintein-Somaticos
Exercício de Somáticos - Vinicius Garcia Rodolfo

# Instalar softwares
sratoolkit, bwa, samtools, bedtools
``` bash
brew install sratoolkit bwa samtools bedtools
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


## Instalar GATK
```bash
wget -c https://github.com/broadinstitute/gatk/releases/download/4.2.2.0/gatk-4.2.2.0.zip
```
```bash
unzip gatk-4.2.2.0.zip
```

## Download dos arquivos

WP312
```bash
time parallel-fastq-dump --sra-id SRR8856724 \
--threads 10 \
--outdir ./ \
--split-files \
--gzip
```
chr9 - hg19
```bash
wget -c https://hgdownload.soe.ucsc.edu/goldenPath/hg19/chromosomes/chr9.fa.gz
```
```bash
gunzip chr9.fa.gz
```
```bash
bwa index chr9.fa
```
```bash
samtools faidx chr9.fa
```


## Alinhamento
```bash
NOME=WP312; Biblioteca=Nextera; Plataforma=illumina;
bwa mem -t 10 -M -R "@RG\tID:$NOME\tSM:$NOME\tLB:$Biblioteca\tPL:$Plataforma" chr9.fa SRR8856724_1.fastq.gz SRR8856724_2.fastq.gz | samtools view -F4 -Sbu -@2 - | samtools sort -m4G -@2 -o WP312_sorted.bam
```

Remover duplicatas de PCR
```bash
samtools rmdup WP312_sorted.bam WP312_sorted_rmdup.bam
```

