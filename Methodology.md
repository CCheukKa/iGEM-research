## Preface
As per the [prime candidates](Methicillin%20resistance/genes/genes%20involved.md#Prime%20candidates) of the [genes involved](Methicillin%20resistance/genes/genes%20involved.md), [mecA](Methicillin%20resistance/genes/mecA%20gene%20(PBP2a).md) and [femA](Methicillin%20resistance/genes/femA%20gene.md) will be selected for detection. The presence of both genes is necessary for [methicillin resistance](Methicillin%20resistance/Genomic%20basis%20for%20methicillin%20resistance.md) expression as shown [here](Methicillin%20resistance/Methicillin%20resistance%20mechanisms.md#PBP2a%20+%20..?).
From [MRSA genome comparison](Methicillin%20resistance/DNA%20sequences/MRSA%20genome%20comparison.md), we found that the gene sequence is specific enough that virtually any 15bp detection site would yield a unique match throughout the entire genome.

## Strategies
There are currently 2 proposed [methicillin resistance](Methicillin%20resistance/Genomic%20basis%20for%20methicillin%20resistance.md) detection strategies:
1. Construct 2 separate DNAzymes each responsible for individually detecting [mecA](Methicillin%20resistance/DNA%20sequences/mecA%20sequence.md) and [femA](Methicillin%20resistance/DNA%20sequences/femA%20sequence.md). The results would then be manually *and*'d together to produce a verdict.
2. Construct 1(+) DNAzyme(s) with one binding site targeting [mecA](Methicillin%20resistance/DNA%20sequences/mecA%20sequence.md) and the other [femA](Methicillin%20resistance/DNA%20sequences/femA%20sequence.md). A positive result can only be seen if both genes are present.

=> I have made an executive decision to focus on strategy 1 since it should have a smaller chance of erroneous error comparatively. As discussed [here](Methicillin%20resistance/DNA%20sequences/MRSA%20genome%20comparison.md#findings), virtually any 15bp is enough to characterise the genes. For the ease of design and testing, we will start with constructing a DNAzyme with *only 1 detection arm*.

## Experimental Design
### DNAzyme design
> - [Medium Scale Integration of Molecular Logic Gates in an Automaton](research%20paper%20pdfs/Medium%20Scale%20Integration%20of%20Molecular%20Logic%20Gates%20in%20an%20Automaton.pdf)
> - [DNAzymes - Methods and Protocols](research%20paper%20pdfs/DNAzymes%20-%20Methods%20and%20Protocols.pdf) (pp.47-63)

![](attachments/Pasted%20image%2020230804204856.png)
-> AND gate is chosen

#### DNAzyme 1 (mecA)
***The terminology below is very much invented by me.***

| Block                | Sequence              | Notes                                           |
|:-------------------- |:--------------------- |:----------------------------------------------- |
| Door left            | CTGAAGAG              |                                                 |
| Detection site left  | TCGTTCTATTCTCAT       | reverse complementary of the first 15bp of mecA |
| Cleavage left        | CTCTTCAG              |                                                 |
| Bowl                 | CGATGACTGCAGTCCACCCAT |                                                 |
| Cleavage right       | GTTAGTGA              |                                                 |
| Detection site right | TTATTCAGTTGTCTC       | reverse complementary of the last 15bp of mecA  |
| Door right           | TCACTAAC              |                                                 |

***Full sequence:*** CTGAAGAGTCGTTCTATTCTCATCTCTTCAGCGATGACTGCAGTCCACCCATGTTAGTGATTATTCAGTTGTCTCTCACTAAC

#### DNAzyme 2 (femA)
***The terminology below is very much invented by me.***

| Block                | Sequence              | Notes                                           |
|:-------------------- |:--------------------- |:----------------------------------------------- |
| Door left            | CTGAAGAG              |                                                 |
| Detection site left  | ATTTGTAAACTTCAT       | reverse complementary of the first 15bp of femA |
| Cleavage left        | CTCTTCAG              |                                                 |
| Bowl                 | CGATGACTGCAGTCCACCCAT |                                                 |
| Cleavage right       | GTTAGTGA              |                                                 |
| Detection site right | CTAAAAAATTCTGTC       | reverse complementary of the last 15bp of femA  |
| Door right           | TCACTAAC              |                                                 |

***Full sequence:*** CTGAAGAGATTTGTAAACTTCATCTCTTCAGCGATGACTGCAGTCCACCCATGTTAGTGACTAAAAAATTCTGTCTCACTAAC

### Interpretation
#### Table
| D1S1 | D1S2 | D2S1 | D2S2 |-| mecA | femA |-| methicillin resistance |
|:----:|:----:|:----:|:----:|-|:----:|:----:|-|:----------------------:|
|  0   |  0   |  0   |  0   |-|  0   |  0   |-|           0            |
|  0   |  0   |  0   |  1   |-|  0   |  0   |-|           0            |
|  0   |  0   |  1   |  0   |-|  0   |  0   |-|           0            |
|  0   |  0   |  1   |  1   |-|  0   |  1   |-|           0            |
|  0   |  1   |  0   |  0   |-|  0   |  0   |-|           0            |
|  0   |  1   |  0   |  1   |-|  0   |  0   |-|           0            |
|  0   |  1   |  1   |  0   |-|  0   |  0   |-|           0            |
|  0   |  1   |  1   |  1   |-|  0   |  1   |-|           0            |
|  1   |  0   |  0   |  0   |-|  0   |  0   |-|           0            |
|  1   |  0   |  0   |  1   |-|  0   |  0   |-|           0            |
|  1   |  0   |  1   |  0   |-|  0   |  0   |-|           0            |
|  1   |  0   |  1   |  1   |-|  0   |  1   |-|           0            |
|  1   |  1   |  0   |  0   |-|  1   |  0   |-|           0            |
|  1   |  1   |  0   |  1   |-|  1   |  0   |-|           0            |
|  1   |  1   |  1   |  0   |-|  1   |  0   |-|           0            |
|  1   |  1   |  1   |  1   |-|  1   |  1   |-|           1            |
