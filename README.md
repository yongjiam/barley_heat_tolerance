## barley_heat_tolerance
```
## selection of candidate genes for gene editing
/Volumes/Elements5T/Dropbox/Chengdao/barley_pangenome_phase2/camila_phenology/
/Users/yongjia/Desktop/workstation/chengdao/heat_tolerance_barley

## selection criteria
significant association with multiple traits in multiple years
gene not reported before
significant CNV in 76 genomes

## blastp in golden promise
(base) ubuntu@yongnectar:/data/barley/goldenPromise$
blastdbcmd -db HC.aa -entry_batch heatPhenology_selectedgene.txt -out heatPhenology_selectedgene.pep.fasta
ln -s /data/barley/morexV3/heatPhenology_selectedgene.pep.fasta
gzip -d *gz
sed -i "s/HORVU.GOLDEN_PROMISE.//" Golden_Promise.primary.protein.fa ## ID too long
makeblastdb -in Golden_Promise.primary.protein.fa -dbtype prot -parse_seqids -out primary_pep
blastp -db primary_pep -query heatPhenology_selectedgene.pep.fasta -outfmt 6 -max_target_seqs 10 -out heatPhenology_selectedgene.pep.blastp

HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.4HG00305850.1	100.000	452	0	0	1	452	1	452	0.0	940
HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.contig_corrected_v1_543G00687780.1	98.673	452	6	0	1	452	1	452	0.0	932
HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.contig_corrected_v1_149G00675950.1	98.673	452	6	0	1	452	1	452	0.0	932
HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.contig_corrected_v1_1012G00674470.1	98.673	452	6	0	1	452	1	452	0.0	932
HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.1HG00073790.1	98.673	452	6	0	1	452	1	452	0.0	932
HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.contig_corrected_v1_736G00690310.1	95.796	452	19	0	1	452	45	496	0.0	904
HORVU.MOREX.r3.4HG0338800.1	HORVU.GOLDEN_PROMISE.PROJ.5HG00459150.1	95.796	452	19	0	1	452	1	452	0.0	904
HORVU.MOREX.r3.1HG0077550.1	HORVU.GOLDEN_PROMISE.PROJ.1HG00069660.1	99.708	343	1	0	1	343	1	343	0.0	694
HORVU.MOREX.r3.5HG0506780.1	HORVU.GOLDEN_PROMISE.PROJ.5HG00452690.1	99.712	347	1	0	1	347	1	347	0.0	706
HORVU.MOREX.r3.5HG0506780.1	HORVU.GOLDEN_PROMISE.PROJ.7HG00588410.1	95.129	349	15	1	1	347	1	349	0.0	680
HORVU.MOREX.r3.4HG0336690.1	HORVU.GOLDEN_PROMISE.PROJ.4HG00303960.1	98.603	358	3	1	1	358	1	356	0.0	722
HORVU.MOREX.r3.4HG0408000.1	HORVU.GOLDEN_PROMISE.PROJ.4HG00366780.1	100.000	207	0	0	1	207	1	207	2.79e-153	423
HORVU.MOREX.r3.4HG0408000.1	HORVU.GOLDEN_PROMISE.PROJ.4HG00366760.1	100.000	207	0	0	1	207	1	207	2.79e-153	423

awk '{print $2}' heatPhenology_selectedgene.pep.blastp.tab > selected_gene_goldenPromise.txt
seqkit grep -n -f selected_gene_goldenPromise.txt Golden_Promise.primary.cds.fa > selected_gene_goldenPromise.cds.fasta
```

