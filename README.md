# Contrast-Enhancement
 Histogram Equalization and its extension

* ������ͼ����ĵ�һ����ҵ������Ǹ�����ɵģ�����ƪ���Ĳ���ʵ�ָ��˰˸�Сʱ�����ʣ����Сʱд���棬����Ϊ�Լ�Ӣ��ˮƽ�ż����ݲݽ�β�����˼����ӡ��ѿ�����

* ��ʽ��������ʾ�����⣬����ת�����ͣ�[chongjg.com](http://chongjg.com/2020/03/12/ContrastEnhancement/)

## 0.����˵��

* ����`grad,logGrad,CACHE_BP,CACHE_RG,CACHE_DP`�����������ͼƬ����ȳߴ��Ȩֵ����

* `CACHE_BP,CACHE_RG,CACHE_DP`�������Դ���ڶ�������Ϊ`ture`����ú�������ʾһ���ĸ�ͼƬ��`figure`���㷨�е�$$\varphi_l$$������ӻ���������ڶ���������Ĭ��Ϊ`false`��������ʾ��

* `GHE,HE_Voting,HE_Contrast,HE_Neighborhood`���������صó�ʹ����ӦHE�㷨��õ��Ľ��ͼƬ�����ҿ�����`figure`�������ʾ��

* `GHE,HE_Voting,HE_Contrast`�����ڶ���������ʾ��ÿ���������õ�������ֱ��ͼͳ�Ƶ�Ȩֵ��

* `GHE,HE_Voting,HE_Contrast,HE_Neighborhood`���������һ�����ز�����������Ϊ`false`����ʾ����������в���Ҫ��ʾ���ͼƬ��`figure`���ò���Ĭ��Ϊ`ture`����

## 1.Histogram Equalization

* ����㷨���**HE**����**GHE(Global ~)**

* �㷨��˼��ǳ��򵥣�һ���Ҷ�ͼ��ֱ��ͼ�����ǲ����ȵģ������Աȶ��������ߣ�����Ҫ���ܹ�ʹ����ֱ��ͼ��ø��Ӿ��ȣ�����ÿ���Ҷ�ֵ�����ظ���һ�������ĶԱȶ�Ӧ�û�ȽϺã���

* �������������ҵ�һ��ͼƬ�Լ�����ֱ��ͼ��

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/origin.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/origin-hist.jpg)

* ����ͼ��ֱ��ͼ�п��Կ��������صķֲ��ǳ������ȣ�����������ض��ǻҶ�ֵ��С�ġ�

* ͨ�׵ؽ���**HE**�㷨��˼�������ֱ��ͼ��ÿ�����ӽ��в��ı�˳����ƶ������Ժϲ������ܲ�֣���ʹ��ÿ�����ӵĸ߶Ⱥ���ռ�õĻҶ����൱��

* ���㷨ʵ���Ͻ�����$$cnt(i),(0\leq i\leq 255)$$��ʾͼ��ÿ���Ҷ�ֵ������������$$sum(i)$$��$$cnt$$��ǰ׺�͡���ôֻ��Ҫ��ԭ���ĻҶ�ֵ$$i$$�ĳ��µĻҶ�ֵ$$sum(i)*255/sum(N)$$���ɡ�

* �㷨�Ľ������ͼ��ʾ

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/GHE.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/GHE-hist.jpg)

* �������Եؿ���ֱ��ͼ�����ӱ��ƶ��ø������ˣ�Ҳ�������ӵĸ߶Ⱥ�ռ�ĻҶ����������ˡ�

* Ȼ����Ҳ�������Կ�������㷨�Ĳ��㣬ͼ�������ֽ紦�Աȶȱ�������ǿ�������Ͱ������ڲ��ĶԱȶȲ�û�еõ��ܺõ���ǿ����ֱ��ͼ�Ͽ��Կ�������ʹ��HE�㷨ʱ�����ͼ���д��ڷǳ����ĳ���Ҷ�ֵ�����أ���ô�ͻᵼ�·ǳ���ĻҶ�ֵ���ܱ�ʹ�ã��Ӷ���Щ�ط��Աȶȹ����Եò���Ȼ�����еĵط��Աȶ���û�ܵõ��ܺõ���ߡ�

* Ϊ�˽��������⣬������Ҫ�ҵ�һ���ѡ����ӡ���ֵķ�����

## 2.Neighborhood Metrics

* ��һ����������������[Image Contrast Enhancement using Bi-Histogram Equalization with Neighborhood Metrics][1]

* ������β�����ӣ�ʵ���Ͼ��ǿ�����ô����������������ط���Ȩֵ����һ������Ȼ�����Ҷ�ֵ��ʱ��Ϳ��Բ���ȫ����һ�������ҿ��԰���Ȩֵ����������õ����ûҶ�ֵ��߶Աȶȡ�

#### 2.1 Voting Metric

* �����������ᵽ��һ���㷨���ܺ���⣬���ǿ��Լ�����Χ$$8$$�����أ����Լ��ڵ��ж��ٸ���������߶Աȶȵ�ԭ����Χ���Լ��ڵ�Խ�࣬��Ӧ���������ﾡ��������׵���ɫ��

* ���Կ���ÿ����������һ��Ȩֵ��Ȼ��ÿ�����Ӹ���Ȩֵ�ڲ�����ÿ����������ֳ�$$9$$�Σ����Ч������ͼ����֮���ٶ���Щ��ֵ����ӽ���HE�㷨���ɡ�

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/Voting-1.png)

* ��������˼����Եõ����½��

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/HE-Voting.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/HE-Voting-hist.jpg)

* ���Կ����������ͼ�У���ߵ����Ӹ߶Ȼ���û�䣬������Ϊ������Χ�����б����ڵģ����Դ��ڵ�����������㷨���޷�����֣������Կ����Ҷ�ֵ�ϴ������õ���һ����ƽ����������ͼƬ����˵û�����ۿɼ��仯��

#### 2.2 Contrast Difference Metric

* ����㷨���ڸո��㷨�Ļ����Ͻ����ٴβ�֣�$$2.1$$�ܹ���һ�����Ӳ�����$$9$$����������㷨�ڸո�**�����Ļ�����**�ٽ��в�֡�

* ����㷨�Ǽ�����Χ���Լ��Ҷ�ֵС������ƽ�����Լ�С���٣��Լ����Լ��������ƽ�����Լ�����٣��ֱ����$$left\;average\;difference(L.a.d)$$��$$right\;average\;difference(R.a.d)$$��

* ����һ����ֵ����$$L.a.d<Threshold<R.a.d$$ʱȨֵ����Ϊ$$1$$����$$L.a.d>Threshold>R.a.d$$ʱȨֵ����Ϊ$$3$$������Ϊ$$2$$��

* ���Ч������ͼ��ʾ

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/Contrast-1.png)

* ��������˼��ʵ�֣����Եõ����½��

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/HE-Contrast.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/HE-Contrast-hist.jpg)

* Ȼ���ܲ��ҵ��ǣ�����Ľ�Ч����΢������������һ����

#### 2.3 Neighborhood Distinction Metric

* ����㷨�ۺ������������㷨������һ�����Ӽ򵥵�ʵ�ַ�ʽ��ֱ�Ӹ�ÿ�����ط���ȨֵΪ��Χ�Ҷ�ֵ����С������������ĺͣ�����һ��һ����������ܹ������Ϊ$$2041$$�������ˡ�

* ��������˼��ʵ�ֵõ����½��

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/HE-Neighborhood.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/HE-Neighborhood-hist.jpg)

* ���Կ�����ֱ��ͼ�Ҳ����ڸ�ϸ�Ĳ��ʹ�ûҶȷֲ����ӵ�ƽ���ˡ�ֻ����ͼƬ����Ȼû��̫�����֡�

#### 2.4 �ܽ�

* ��������Կ����������������������߶Աȶ��ǲ����ģ���ͼƬ��ĳһЩ���ػҶ�ֵȫ��һ����ȴ������κ������ʱ����Щ���ػ�ռ�ô����ĻҶ�ֵ���䣬ȴ����ͼ��Ч���������ס�Ϊ�˸ı���һ״��������Ҫ��һЩ����Ҫ�����غ��ԣ���һЩ��Ҫ���������ؿ��ǡ�

## 3.Pixel Weight

* ����$$2.4$$��˼����ԭ�����ǽ���ֱ��ͼͳ��ʱ��һ��������һ�������������صĶ���������Ӧ��ռ���ٻҶ�ֵ��Ȼ��һ��ͼƬ�п��ܺܶ����ض���û������ģ�����һ��������ĺ�ɫ�����������ֺ�ɫ��ͦ�ã�����Ҫ���ǸĽ����ĶԱȶȡ�������ǿ��Ը���������Ȩ�أ��еĲ���Ҫ�����ؿ�����������������еĺ���Ҫ�����ؿ�������������ȵȡ�����Ȩ�ص����þͳ���һ���о������⡣

* ������һ�����Ҫ���ǣ�HE�Լ�$$2.1,2.2$$���㷨�������������Ȩֵ������ͻ��Ҳ����˵���ǿ����������ϲ�ַ�����Ȩֵ������

#### 3.1 Gradient

* ͨ����Ϊͼ��ı�Ե�ṩ��Ϣ�����ǿ��Կ���ʹ���ݶ���Ϊ���ص�Ȩֵ����ַ�ʽѡ��$$2.2$$�����Ϊ

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/Grad-HE-Contrast.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/Grad-HE-Contrast-hist.jpg)

* ���Ժ����ԵĿ���ͼ��Աȶ����֮ǰ���˽ϴ����������ֱ��ͼҲ���Կ���ռ�д󲿷����ص�������Ӳ���ռ�д�Ƭ�ĻҶ�ֵ������ʹ��������ĶԱȶȵõ�����ǿ��

#### 3.2 log Gradient

* ����뷨�ǹ۲쵽�е������ݶȹ���Ϊ�����Ƶ�������Ȩֵ�������ǿ���ʹ��$$\log(gradient+1)$$�ķ�ʽ����ݶȡ���ϲ�ַ�ʽ$$2.2$$�������Ϊ

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/logGrad-HE-Contrast.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/logGrad-HE-Contrast-hist.jpg)

* �Ա�$$3.1$$���Է���ͼ���������ȵõ���ߣ��ܶ�ԭ����ȫ��������ϸ��Ҳ��ʼչ�ֳ������Ѿ��ﵽ�˱ȽϺõ�Ч����

#### 3.3 CONTRAST-ACCUMULATED

* ���������������[CONTRAST-ACCUMULATED HISTOGRAM EQUALIZATION FOR IMAGE ENHANCEMENT][2]

* ʵ�����㷨�Ĳ���ܼ򵥣�($$S,L,\epsilon$$ΪԤ�����)

* ��һ������ͼƬ$$\mathbf A$$�ȱ�������ʹ�С�����С��Ϊ$$S$$�õ�ͼƬ$$\mathbf B_1$$(��д����ʱֱ��������Ϊ$$S$$)

* �ڶ�������ͼƬ$$\mathbf B_1$$������������$$2$$�õ�$$\mathbf B_2$$���Դ�����ֱ��$$\mathbf B_L$$��

* ��������

$$\varphi_l(q)=-\sum_{q'\in \mathcal N(q)}\min\Big(\frac{\mathbf B_l(q)-\mathbf B_l(q')}{255},0\Big),(l=1,...,L)$$

* ����$$q$$��ͼ���еĶ�ά���꣬$$\mathcal N(q)$$��$$q$$�������پ����µĽ��ڣ�����ȡ���������ĸ���

* ���Ĳ�����$$\varphi_l(q)$$ͨ��˫���β�ֵ�任��ԭͼ��$$\mathbf A$$�Ĵ�С������$$\varphi_l'(x,y)$$��

* ���岽��ȨֵΪ

$$\Phi(x,y)=\Bigg(\prod_{l=1}^L\max(\varphi_l'(x,y),\epsilon)\Bigg)^{\frac{1}{L}}$$

* ���ݾ��飬$$S$$ȡ$$256$$��$$L$$ȡ$$4$$��$$\epsilon$$ȡ$$0.001$$��

* ���Եõ�$$L$$��$$\varphi_l(q)$$������

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/CACHE-DP-HE-Contrast-phi.jpg)

* ʹ������������$$2.2$$�������Ϊ

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/CACHE-DP-HE-Contrast.jpg)

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/CACHE-DP-HE-Contrast-hist.jpg)

* �������ͼ�����㷨���պ�$$3.2$$Ч����ࡣ

* ����Ҫע�����$$\varphi(q)$$��������ʽҲ�ǿ��Ա任�ģ���ǰ������ʽ����ΪĳЩ��Ҫ����Ϣ���������ں�ɫ�еģ������Ϊ��Ҫ��Ϣ���������ڰ�ɫ�У������޸�$$\varphi$$��������

$$\varphi_l(q)=\sum_{q'\in \mathcal N(q)}\max\Big(\frac{\mathbf B_l(q)-\mathbf B_l(q')}{255},0\Big),(l=1,...,L)$$

* ���⻹��һ����ʽ�������Բ��ģ���һ����ȷ��

$$\varphi_l(q)=\frac{\vert\mathbf B_l(q_{left})-\mathbf B_l(q_{right})\vert+\vert\mathbf B_l(q_{top})-\mathbf B_l(q_{down})\vert}{255},(l=1,...,L)$$

## 4.Ԥ����

* �������źŴ����У�Ԥ������һ�����õ�Ԥ�����ɣ������������ǲ���ͼ��Ҳ����Ԥ���أ����ǰѸ�Ƶ������ǿ����Ƶ�������ơ���ֻ������һ���򵥵ĳ��ԣ���������ά����Ҷ�任��Ȼ��ֱ�Ӹ���Ƶ��λ��$$x,y$$�����ĵĹ�һ���������$$0.5$$��Ϊ�˲�Ȩֵ��

* ���ĶԱ�����ͼ��ʾ�����û��Ԥ�����Ҳ���Ԥ�������ִ���㷨��

![](https://raw.githubusercontent.com/chongjg/chongjg.github.io/master/img/Contrast-enhancement/add-freq.jpg)

* ������ô�ԱȲ��Ǻ����ԣ������ڵ������غ�����ͼƬ�����л�ʱ���ܹ������Եؿ����Ҳ��ͼƬϸ�ڲ��ֱ������ˡ�������ϸ�۲������ϵ������Ҳ�ͼƬ��������Ҫ����������ܶ�ġ���ȻҲ��һ�����ͼ�������Ҳ����ǿ�ˣ��������ĸо��ͺ����ǣ�����ͼ�����Ҳ��ͼ����һ��ƽ���˲���

## 5.�ܽ�

* �ܵ���˵��������Ч����õĴ���Ӧ���ǣ�Ƶ��Ԥ����+��ַ���$$2.2$$+Ȩֵ����$$3.3$$���������������ʱ��Ч���ǱȽϵ͵ġ�

* Ƶ��Ԥ����ʱ�临�Ӷȣ�$$O(MN\log(MN))$$

* ���$$2.1$$��$$2.2$$ʱ�临�Ӷȣ�$$O(MNm^2)$$��$$m$$����Χͳ�Ʒ�Χ��

* ���$$2.3$$ʱ�临�Ӷȣ�$$O(MN\log(MN))$$

* �ݶ�Ȩֵ�������ݶ�Ȩֵʱ�临�Ӷȣ�$$O(MNl^2)$$��$$l$$�Ǽ����ݶȵľ���˴�С��

* **CACHE**ʱ�临�Ӷȣ�$$O(MNL)$$�������Ƚϴ�

* ����Ϊʹ��MATLABÿ���������10�ε���ʱ�䣬��λ�룬����ʹ��$$1023\times 682$$��ͨ��ͼ�񡣣����ų��Ҹ��˴���д���ӵ����أ�

<table>
	<tr>
	    <td colspan="2" rowspan="3"> </td>
	    <td colspan="8">����㷨</td>
	</tr>
	<tr>
		<td colspan="2">HE</td>
		<td colspan="2">Voting</td>
		<td colspan="2">Contrast</td>
		<td colspan="2">Neighborhood</td>
	</tr>
	<tr>
		<td>������</td>
		<td>Ԥ����</td>
		<td>������</td>
		<td>Ԥ����</td>
		<td>������</td>
		<td>Ԥ����</td>
		<td>������</td>
		<td>Ԥ����</td>
	</tr>
	<tr>
	    <td rowspan="4">Ȩֵ�㷨</td>
	    <td> ȫ���</td>
	    <td> 0.1996</td>
	    <td> 2.2534</td>
	    <td> 1.2470</td>
	    <td> 3.1890</td>
	    <td> 3.4760</td>
	    <td> 5.8460</td>
	    <td rowspan="4"> 3.1830</td>
	    <td rowspan="4"> 5.6290</td>
	</tr>
	<tr>
	    <td> Grad</td>
	    <td> 0.4920</td>
	    <td> 2.6180</td>
	    <td> 1.2600</td>
	    <td> 3.5220</td>
	    <td> 3.6800</td>
	    <td> 6.2100</td>
	</tr>
	<tr>
	    <td> logGrad</td>
	    <td> 0.5970</td>
	    <td> 2.8120</td>
	    <td> 1.5480</td>
	    <td> 3.6590</td>
	    <td> 4.0660</td>
	    <td> 6.2440</td>
	</tr>
	<tr>
	    <td> CACHE</td>
	    <td> 5.3010</td>
	    <td> 7.7910</td>
	    <td> 6.1620</td>
	    <td> 7.9590</td>
	    <td> 8.1010</td>
	    <td> 10.5540</td>
	</tr>
	
</table>

* ���ݾ���ĳ�����Ҫ����ѡ��ͬ����ϣ������۹۲������˵��**�����ݶ�Ȩֵ�Ӿ���HE�㷨**Ч���Ѿ��ǳ������ˣ������ٶ��϶���1023*682�ĵ�ͨ��ͼƬ�ܹ��ﵽ��Լÿ��17֡��Ч���Ѿ��ܲ����ˡ��������һЩϸ�ڲ����и��ߵ�Ҫ����Կ��Ǽ���Ԥ��������ע������Ҳ������һ��������

## 6.�ο�

[1] [Image Contrast Enhancement using Bi-Histogram Equalization with Neighborhood Metrics][1]

[2] [CONTRAST-ACCUMULATED HISTOGRAM EQUALIZATION FOR IMAGE ENHANCEMENT][2]

  [1]:https://www.researchgate.net/publication/224209864_Image_Contrast_Enhancement_using_Bi-Histogram_Equalization_with_Neighborhood_Metrics?enrichId=rgreq-319bc3ef6eb4fa0f9f562c5ffd925e65-XXX&enrichSource=Y292ZXJQYWdlOzIyNDIwOTg2NDtBUzo0NTY1MTE5MTU4NTk5NjhAMTQ4NTg1MjMzMDAzOQ%3D%3D&el=1_x_3&_esc=publicationCoverPdf
  [2]:https://www.researchgate.net/publication/323349746_Contrast-accumulated_histogram_equalization_for_image_enhancement?enrichId=rgreq-3df2813a03f08e26ebb9c7759f0a5618-XXX&enrichSource=Y292ZXJQYWdlOzMyMzM0OTc0NjtBUzo1OTg4OTc1NDYyNDAwMDFAMTUxOTc5OTcxMDA5Mg%3D%3D&el=1_x_3&_esc=publicationCoverPdf