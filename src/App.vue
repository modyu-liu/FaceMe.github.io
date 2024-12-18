<script setup lang="ts">
import { ImgComparisonSlider } from '@img-comparison-slider/vue'
import { onMounted } from 'vue';
onMounted(() => {
  // 确保MathJax已加载并渲染公式
  if (window.MathJax) {
    window.MathJax.typeset(); // 重新渲染页面中的数学公式
  }
});
</script>

<template>

  <div class="content">
  <h1 style="text-align: center; font-size: 36px;"><strong>FaceMe: Robust Blind Face Restoration With Personal Identification</strong></h1>
  
  <p id="authors" style="text-align: center;">
    <a href="" style="font-size: 28px;" >Siyu Liu<sup>1,*</sup></a>, 
    <a href="https://adam-duan.github.io/" style="font-size: 28px;" >Zheng-Peng Duan<sup>1,*</sup></a>, 
    <a href="" style="font-size: 28px;" >Jia OuYang<sup>3</sup></a>, 
    <a href="" style="font-size: 28px;" >Jiayi Fu<sup>1</sup></a>,<br>
    <a href="" style="font-size: 28px;" >Hyunhee Park<sup>4</sup></a>, 
    <a href="" style="font-size: 28px;" >Zikun Liu<sup>3</sup></a>,
    <a href="https://scholar.google.com/citations?user=RZLYwR0AAAAJ&hl=zh-CN&oi=ao" style="font-size: 28px;" >Chun-Le Guo<sup>1,2,&dagger;</sup></a>,
    <a href="https://li-chongyi.github.io/" style="font-size: 28px;">Chongyi Li<sup>1,2</sup></a>,
    <br><br>

    <span style="font-size: 20px; font-weight: bold; ;"><sup>1</sup>VCIP, CS, Nankai University, </span>
    <span style="font-size: 20px; font-weight: bold; ;"><sup>2</sup>NKIARI, Shenzhen Futian</span> <br>
    <span style="font-size: 20px; font-weight: bold; ;"><sup>3</sup>Samsung Research, China, Beijing (SRC-B)</span> <br>
    <span style="font-size: 20px; font-weight: bold; ;"><sup>4</sup>The Department of Camera Innovation Group, Samsung Electronics</span> <br>
    <span style="font-size: 20px; font-weight: bold; ;"><sup>*</sup>Equal contribution. <sup>&dagger;</sup>Corresponding author.</span> <br>
    
  </p>
  
  <p style="text-align: center; font-size: 1.5em;">
      <a href="" target="_blank">[Paper]</a>&nbsp;&nbsp;&nbsp;&nbsp;
      <a href="" target="_blank">[Code]</a>&nbsp;&nbsp;&nbsp;&nbsp;
      <a href="" target="_blank">[Dataset]</a>&nbsp;&nbsp;&nbsp;&nbsp;
      <a href="" target="_blank">[Demo]</a>
  </p>

  <figure>
    <img src="/FaceMe_files/teaser.png" alt="Teaser image" style="width: 100%;">
  </figure>
  
  <h4 style="text-align: center; font-style: italic;">
    Make the people in the photo look like you and those you are familiar with. Using a single or a few reference images,
    we can restore realistic images without any fine-tuning for identity. 
  </h4>
  
  <img src="/FaceMe_files/demo.gif" alt="Example GIF" style="width: 100%;">
  <h4 style="text-align: center; font-style: italic;">
    FaceMe can effectively maintain identity consistency as
    degradation level increases, while also balancing the dependency between the low-quality input and the reference image.
  </h4>

 
  <div class="row">
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/pair_result/chan/degraded_level_6.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/pair_result/chan/chan.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/pair_result/huang/degraded_level_9.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/pair_result/huang/huang3.png"
      />
    </ImgComparisonSlider>
  </div>

  <div class="row">
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/pair_result/Taylor/lq.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/pair_result/Taylor/20241217143046.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/pair_result/trump/degraded_level_9.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/pair_result/trump/trump.png"
      />
    </ImgComparisonSlider>
  </div>

  <div class="row">
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/pair_result/zhou/degraded_level_9.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/pair_result/zhou/20241217133023.png"
      />
    </ImgComparisonSlider>
  </div>


  </div>

<div class="content">
  <h2 style="text-align:center;">Abstract</h2>
  <p>Blind face restoration is a highly ill-posed problem due to the lack of necessary context. Although existing methods produce high-quality outputs, they often fail to faithfully preserve the individual's identity. In this paper, we propose a personalized face restoration method, FaceMe, based on a diffusion model. Given single or a few reference images, we use an identity encoder to extract identity-related features, which serve as prompts to guide the diffusion model in restoring high-quality and identity-consistent facial images. By simply combining identity-related features, we effectively minimize the impact of identity-irrelevant features during training and supports any number of reference image inputs during inference. Additionally, thanks to the robustness of the identity encoder, synthesized images can be used as reference images during training, and identity changing during inference does not require fine-tuning the model. We also propose a pipeline for constructing a reference image training pool that simulates the poses and expressions that may appear in real-world scenarios. Experimental results demonstrate that our FaceMe can restore high-quality facial images while maintaining identity consistency, achieving excellent performance and robustness. </p>
</div>
<!-- <div class="content">
  <h2>Background</h2>
  <p> Given a particular subject such as clock (shown in the real images on the left), it is very challenging to generate it in different contexts with state-of-the-art text-to-image models, while maintaining high fidelity to its key visual features. Even with dozens of iterations over a text prompt that contains a detailed description of the appearance of the clock (<em>"retro style yellow alarm clock with a white clock face and a yellow number three on the right part of the clock face in the jungle"</em>), the Imagen model [Saharia et al., 2022] can't reconstruct its key visual features (third column). Furthermore, even models whose text embedding lies in a shared language-vision space and can create semantic variations of the image, such as DALL-E2 [Ramesh et al., 2022], can neither reconstruct the appearance of the given subject nor modify the context (second column). In contrast, our approach (right) can synthesize the clock with high fidelity and in new contexts (<em>"a [V] clock in the jungle"</em>).</p>
  <br>
  <img class="summary-img" src="/ DreamBooth_files/background.png" style="width:100%;"> <br>
</div> -->
<div class="content">
  <h2 style="text-align:center;">Method</h2>
  <p>FaceMe is a fine-tuning-free personalized blind face restoration method based on diffusion model. Given a low-quality input and either single or a few high-quality references images of the same identity, FaceMe restores high-quality facial images and maintains identity consistency within seconds. </p>
  <br>
  <figure>
    <img src="/FaceMe_files/overview.png" alt="Overview image" style="width: 100%;">
  </figure>
  <p>
    For the proposed FaceMe, identity-related features from the reference image are extracted by an identity encoder, 
    simply combined to support multi-reference image inputs. We use a fixed text, 
    <i>i.e., "a photo of a face."</i>, and the combined identity-related features replace the embedding corresponding to 
    <i>"face."</i> The updated embeddings are sent to the cross-attention layer of the diffusion model to guide personalized face image restoration.
  </p>
  <p>
    To address the challenge of insufficient datasets for personalized blind face restoration, we utilize synthetic facial images as reference images to build our training data pool.
    We synthesize multiple reference facial images of the same identity as the given facial image using Arc2Face (Papantoniou et al. 2024), equipped with ControlNet (Zhang,Rao, and Agrawala 2023). 
    Given a pair of facial images (\(x_{ref} , x_{pose}\)), Arc2Face can synthesize facial images that maintain the identity of \(x_{ref}\) and the pose of \(x_{pose}\).
    We divide the FFHQ dataset into several subsets based on expressions and poses. 
    For each image synthesis, a facial image is randomly selected from each subset to serve as the pose reference \(x_{pose}\).
  </p>
</div>

  <div class="content">
    <h2 style="text-align:center;">Results</h2>
    <h2>Quantitative Comparisons</h2>
    <figure>
      <img src="/FaceMe_files/Quantitative_Comparisons.png" alt="Quantitative_Comparisons" style="width: 100%;">
    </figure>
    <p>
    FaceMe achieves the best performance in PSNR, FID, LMD, and IDS, and the second-best performance in LPIPS. 
    It is worth noting that FaceMe has significantly improved in both LMD and IDS, which demonstrates its ability in personalization while minimizes the impact of ID-irrelevant features. 
    </p>
    <h2>Visual Comparisons</h2>
    <figure>
      <img src="/FaceMe_files/synth_result.png" alt="synth_result" style="width: 100%;">
    </figure>
    <figure>
      <img src="/FaceMe_files/real_result.png" alt="real_result" style="width: 100%;">
    </figure>
  </div>

  <div class="content">
    <h2 style="text-align:center;">Interactive Comparison</h2>
  <!-- 1 -->
  <div class="row">
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/Danny_Green_0001.jpg"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/Danny_Green_0001.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/Svend_Aage_Jensby_0001.jpg"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/Svend_Aage_Jensby_0001.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/Vaclav_Havel_0001.jpg"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/Vaclav_Havel_0001.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/Yasushi_Chimura_0001.jpg"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/Yasushi_Chimura_0001.png"
      />
    </ImgComparisonSlider>
  </div>
  <!-- 2 -->
  <div class="row">
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/00016_00.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/00016_00.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/00101_00.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/00101_00.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/10008_02.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/10008_02.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/10009_02.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/10009_02.png"
      />
    </ImgComparisonSlider>
  </div>
  <!-- 3 -->
  <div class="row">
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/0761.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/0761.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/0032.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/0032.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/0909.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/0909.png"
      />
    </ImgComparisonSlider>
    <ImgComparisonSlider>
      <img
        slot="first"
        style="width: 100%"
        src="/FaceMe_files/compare_result/lq/0285.png"
      />
      <img
        slot="second"
        style="width: 100%"
        src="/FaceMe_files/compare_result/sr/0285.png"
      />
    </ImgComparisonSlider>
  </div>
  <p>
        You can slide the images to clearly observe the differences between the input on the left and the output on the right. 
        The first row is from the LFW-Test; the second row is from the WebPhoto-Test; 
        and the third row is from the Wider-Test. 
        FaceMe can restore high-fidelity and high-quality images, while previous methods produce the unrealistic artifacts.
    </p>
</div>


  <div class="content">
    <h2 style="text-align: center;">BibTex</h2>
    <!-- <code> @article{ruiz2022dreambooth,<br>
    &nbsp;&nbsp;title={DreamBooth: Fine Tuning Text-to-image Diffusion Models for Subject-Driven Generation},<br>
    &nbsp;&nbsp;author={Ruiz, Nataniel and Li, Yuanzhen and Jampani, Varun and Pritch, Yael and Rubinstein, Michael and Aberman, Kfir},<br>
    &nbsp;&nbsp;booktitle={arXiv preprint arxiv:2208.12242},<br>
    &nbsp;&nbsp;year={2022}<br>
    } </code>  -->
  </div>

  <div class="content">
    <h4>Acknowledgements</h4>
    <p style="font-size: 15px; font-weight: bold;">This work is funded by the National Natural Science Foundation of China (62306153) and the Fundamental Research Funds for the Central Universities (Nankai University, 07063243143). 
      The computational devices of this work is supported by the Supercomputing Center of Nankai University (NKSC). 
    </p>
    <p style="font-size: 15px; font-weight: bold;">
      We sincerely thank our friend <a href="https://github.com/Men1scus">Ziheng Zhang</a> for his assistance in developing this website.
    </p>
    

  </div>

  <footer class="footer">
    <div class="container">
      <div class="columns is-centered">
        <!-- <div class="column is-8"> -->
            <p>
              This website's source code is borrowed from the <a
              href="https://github.com/google/dreambooth">DreamBooth</a> project page.
            </p>
        <!-- </div> -->
      </div>
    </div>
  </footer>

</template>

<style scoped>
.row {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}
.row img-comparison-slider {
  flex: 1;
}
a, a:visited {
  color: #224b8d;
  font-weight: 300;
}
.content img {
  display: inline-block; /* 保持图片为行内块元素 */
}
.content {
  font-size: 21px;
  width: 1000px;
  padding: 25px 50px;
  margin: 25px auto;
  background-color: white;
  box-shadow: 0px 0px 10px #999;
  border-radius: 15px;
  font-family: "Google Sans";
  color: #333;
}
</style>
