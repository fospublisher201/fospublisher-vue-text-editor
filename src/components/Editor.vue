<template>
  <body :style="styleObject.editorWidth" class="editorWidth">
    <div class="toolBar">
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('bold')"
      >
        <i class="fas fa-bold"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.bold
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('italic')"
      >
        <i class="fas fa-italic"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.italic
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('underline')"
      >
        <i class="fas fa-underline"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.underline
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('strikethrough')"
      >
        <i class="fas fa-strikethrough"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.strikethrough
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('justifyLeft')"
      >
        <i class="fas fa-align-left"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.justifyLeft
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('justifyCenter')"
      >
        <i class="fas fa-align-center"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.justifyCenter
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('justifyRight')"
      >
        <i class="fas fa-align-right"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.justifyRight
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('justifyFull')"
      >
        <i class="fas fa-align-justify"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.justifyFull
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('cut')"
      >
        <i class="fas fa-cut"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{ word.cut }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('copy')"
      >
        <i class="fas fa-copy"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.copy
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('indent')"
      >
        <i class="fas fa-indent"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.indent
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('outdent')"
      >
        <i class="fas fa-outdent"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.outdent
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('subscript')"
      >
        <i class="fas fa-subscript"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.subscript
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('superscript')"
      >
        <i class="fas fa-superscript"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.superscript
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('undo')"
      >
        <i class="fas fa-undo"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.undo
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('redo')"
      >
        <i class="fas fa-redo"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.redo
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('removeFormat')"
      >
        <i class="fas fa-remove-format"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.removeFormat
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('insertUnorderedList')"
      >
        <i class="fas fa-list-ul"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.unorderedList
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('insertOrderedList')"
      >
        <i class="fas fa-list-ol"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.orderedList
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('insertParagraph')"
      >
        <i class="fas fa-paragraph"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.insertParagraph
        }}</span>
      </button>
      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="execCmd('insertHorizontalRule')"
      >
        HR
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.insertHorizontalRule
        }}</span>
      </button>

      <button
        :style="styleObject.toolButton"
        class="toolButton"
        @click="toggleLinkModal"
      >
        <i class="fas fa-link"></i>
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.link
        }}</span>
      </button>

      <div id="linkModal" class="modal">
        <div :style="styleObject.modalContent" class="modal-content">
          <h2 style="margin-top: 0">Link</h2>
          <input
            :style="styleObject.modalTextInput"
            v-model="pageLink"
            class="modalTextInput"
            type="text"
          />
          <button
            :style="styleObject.modalButton"
            class="modalButton"
            @click="toggleLinkModal"
          >
            OKAY
          </button>
        </div>
      </div>

      <button
        :style="styleObject.toolButton"
        id="emoji-trigger"
        class="toolButton"
      >
        😀
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.emoticon
        }}</span>
      </button>
      <div class="dropdown">
        <button
          @click="toggleDropdown('fontStyleDropdown')"
          class="dropdownButton"
          :style="styleObject.dropdownButton"
        >
          {{ word.fontStyle }} ▾
          <span :style="styleObject.tooltip" class="tooltip">{{
            word.fontStyle
          }}</span>
        </button>
        <div
          id="fontStyleDropdown"
          style="width: 110px"
          class="dropdown-content"
        >
          <div
            v-for="(font, index) in fontStyle"
            :key="index"
            :style="{ 'font-family': [font] }"
            @click="
              [
                execCommandWithArg('fontName', font),
                toggleDropdown('fontStyleDropdown'),
              ]
            "
          >
            {{ font }}
          </div>
        </div>
      </div>
      <div class="dropdown">
        <button
          @click="toggleDropdown('fontSizeDropdown')"
          class="dropdownButton"
          :style="styleObject.dropdownButton"
        >
          {{ word.fontSize }} ▾
          <span :style="styleObject.tooltip" class="tooltip">{{
            word.fontSize
          }}</span>
        </button>
        <div id="fontSizeDropdown" style="width: 97px" class="dropdown-content">
          <div
            v-for="(size, index) in fontSize"
            :key="index"
            @click="
              [
                execCommandWithArg('formatBlock', size),
                toggleDropdown('fontSizeDropdown'),
              ]
            "
          >
            {{ size }}
          </div>
        </div>
      </div>
      <div style="display: inline-block">
        <div :style="styleObject.colorPickerButton" class="colorPickerButton">
          {{ word.fontColor }}
        </div>
        <button :style="styleObject.toolButtonText" class="toolButtonText">
          <input
            class="colorPicker"
            type="color"
            @change="execCommandWithArg('foreColor', $event.target.value)"
          />
          <span :style="styleObject.tooltip" class="tooltip">{{
            word.fontColor
          }}</span>
        </button>
        <div :style="styleObject.colorPickerButton" class="colorPickerButton">
          {{ word.backgroundColor }}
        </div>
        <button :style="styleObject.toolButtonText" class="toolButtonText">
          <input
            class="colorPicker"
            type="color"
            @change="execCommandWithArg('hiliteColor', $event.target.value)"
          />
          <span :style="styleObject.tooltip" class="tooltip">{{
            word.backgroundColor
          }}</span>
        </button>
      </div>

      <button
        :style="styleObject.toolButtonText"
        class="toolButtonText"
        @click="toggleImageModal"
      >
        <i class="fas fa-file-image"></i> {{ word.image }}
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.image
        }}</span>
      </button>

      <div id="imageModal" class="modal">
        <div :style="styleObject.modalContent" class="modal-content">
          <h2 style="margin-top: 0">Image upload</h2>
          <input
            :style="styleObject.modalTextInput"
            class="modalTextInput"
            id="ImageFile"
            type="file"
            accept="image/png, image/jpeg"
          />
          <div style="font-size: 15px; padding-bottom: 5px">Image link</div>
          <input
            :style="styleObject.modalTextInput"
            v-model="imageLink"
            class="modalTextInput"
            type="text"
          />
          <button
            :style="styleObject.modalButton"
            class="modalButton"
            @click="toggleImageModal"
          >
            OKAY
          </button>
        </div>
      </div>

      <button
        :style="styleObject.toolButtonText"
        class="toolButtonText"
        @click="execCmd('selectAll')"
      >
        <i class="fas fa-check"></i>
        {{ word.selectAll }}
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.selectAll
        }}</span>
      </button>
      <button
        v-if="styleObject.pdfButtonShow"
        :style="styleObject.toolButtonText"
        class="toolButtonText"
        @click="exportToPDF()"
      >
        <i class="fas fa-file-pdf"></i> PDF
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.exportPDF
        }}</span>
      </button>
      <button
        v-if="styleObject.wordButtonShow"
        :style="styleObject.toolButtonText"
        class="toolButtonText"
        @click="exportToWord()"
      >
        <i class="fas fa-file-word"></i> Word
        <span :style="styleObject.tooltip" class="tooltip">{{
          word.exportWord
        }}</span>
      </button>
    </div>

    <iframe
      :style="styleObject.editorWidth"
      id="richTextField"
      name="richTextField"
      class="editorWidth"
    ></iframe>
  </body>
</template>

<script>
import { EmojiButton } from "@joeattardi/emoji-button";
import html2pdf from "html2pdf.js";
import jquery from "jquery";
import "@fortawesome/fontawesome-free/js/all.js";
import { langWord } from "@/assets/language";
require("jquery-ui/ui/widgets/draggable");
require("jquery");
require("jquery-ui-bundle");

export default {
  props: {
    styleObject: Object,
    content: String,
    lang: String,
  },
  data() {
    return {
      isInEditMode: true,
      fontSize: ["H1", "H2", "H3", "H4", "H5", "H6"],
      fontStyle: ["돋움", "굴림", "바탕", "궁서", "맑은 고딕"],
      imageFile: [],
      imageLink: "",
      imageNum: 0,
      pageLink: "",
      selectLang: this.lang ? this.lang : "en",
      word: langWord["en"],
    };
  },
  methods: {
    setLanguage() {
      this.word = langWord[this.selectLang];
    },
    // move focus
    setFocus() {
      const iFrame = document.getElementsByName("richTextField");
      jquery(iFrame)
        .contents()
        .find("body")
        .focus();
    },

    // toggle image input modal
    toggleImageModal() {
      const modal = document.getElementById("imageModal");
      if (modal.style.display === "block") {
        modal.style.display = "none";
        const imageFile = document.getElementById("ImageFile").value;
        if (this.imageLink !== "" || imageFile) {
          this.insertImage();
        }
      } else {
        modal.style.display = "block";
      }
    },

    // toggle page link modal
    toggleLinkModal() {
      const modal = document.getElementById("linkModal");
      if (modal.style.display === "block") {
        modal.style.display = "none";
        if (this.pageLink !== "") {
          this.insertLink();
        }
      } else {
        modal.style.display = "block";
      }
    },

    // toggle dropdown function
    toggleDropdown(arg) {
      document.getElementById(arg).classList.toggle("show");
    },

    // insert page link
    insertLink() {
      this.execCommandWithArg("createLink", this.pageLink);

      const links = window.richTextField.document.querySelectorAll("a");

      links.forEach((item) => {
        item.target = "_blank";

        // turn off the iframe design mode to active link function
        item.addEventListener("mouseover", () => {
          window.richTextField.document.designMode = "Off";
        });

        // turn on the iframe design mode after inserting link
        item.addEventListener("mouseout", () => {
          window.richTextField.document.designMode = "On";
        });
      });
      this.pageLink = "";
    },

    // drag and resize image file
    imageDragResize() {
      const vm = this;
      const iframeContents = jquery('iframe[name="richTextField"]').contents();

      // wrap image with <div> and <br> tag
      iframeContents
        .find(`#${vm.imageNum}`)
        .wrap(
          `<div contenteditable="false" id="wrapper${vm.imageNum}" style="text-align: center;"><div id="draggableHelper${vm.imageNum}" contenteditable="false" style="display:inline-block;"></div></div>`
        );

      iframeContents
        .find(`#wrapper${vm.imageNum}`)
        .before("<br>")
        .after("<br><br>");

      // drag function
      iframeContents.find(`#draggableHelper${vm.imageNum}`).draggable({
        containment: window.richTextField.document.getElementsByTagName("body"),
        axis: "x",
      });

      iframeContents.find(`#${vm.imageNum}`).css({
        display: "block",
        margin: "0px auto",
      });

      // resize function
      iframeContents
        .find(`#${vm.imageNum}`)
        .resizable({ aspectRatio: true, minWidth: 300 });

      iframeContents
        .find(`#draggableHelper${vm.imageNum} > .ui-wrapper`)
        .children(".ui-resizable-handle")
        .css({
          position: "absolute",
          "font-size": "0.1px",
          display: "block",
          "-ms-touch-action": "none",
          "touch-action": "none",
        });

      iframeContents
        .find(`#draggableHelper${vm.imageNum} > .ui-wrapper`)
        .children(".ui-resizable-e")
        .css({
          cursor: "e-resize",
          width: "7px",
          right: "-5px",
          top: "0",
          height: "100%",
        });

      iframeContents
        .find(`#draggableHelper${vm.imageNum} > .ui-wrapper`)
        .children(".ui-resizable-s")
        .css({
          cursor: "s-resize",
          height: "7px",
          bottom: "-5px",
          left: "0",
          width: "100%",
        });

      iframeContents
        .find(`#draggableHelper${vm.imageNum} > .ui-wrapper`)
        .children(".ui-resizable-se")
        .css({
          cursor: "se-resize",
          height: "12px",
          bottom: "1px",
          right: "1px",
          width: "12px",
        });

      // mouse enter function
      iframeContents.find(`#${vm.imageNum}`).mouseenter(function(event) {
        event.target.style.cursor = "Move";
        event.target.style.border = "solid grey 1px";
        event.target.style.boxSizing = "border-box";
      });

      // mouse out function
      iframeContents.find(`#${vm.imageNum}`).mouseout(function(event) {
        event.target.style.border = "none";
      });

      // set image number for each image
      vm.imageNum += 1;
    },

    // insert image with file
    insertImage() {
      const imageFile = document.getElementById("ImageFile").files[0];

      this.setFocus();

      if (imageFile) {
        const vm = this;
        const file = imageFile;
        const reader = new FileReader();
        const image = new Image();

        reader.readAsDataURL(file);
        reader.onloadend = function() {
          image.src = reader.result;
        };

        setTimeout(() => {
          this.execCommandWithArg("insertImage", image.src);
        }, 100);

        setTimeout(() => {
          const imgTags = jquery('iframe[name="richTextField"]')
            .contents()
            .find("img");

          imgTags.each(function(index, imgTag) {
            if (imgTag.id === "") {
              imgTag.setAttribute("id", vm.imageNum);
              imgTag.style.maxWidth = 700;
              imgTag.onload = function() {
                vm.imageDragResize();
              };
              document.getElementById("ImageFile").value = "";
            }
          });
        }, 100);

        // insert image with link
      } else if (this.imageLink !== "") {
        this.execCommandWithArg("insertImage", this.imageLink);

        const vm = this;
        const imgTags = jquery('iframe[name="richTextField"]')
          .contents()
          .find("img");

        imgTags.each(function(index, imgTag) {
          if (imgTag.id === "") {
            imgTag.setAttribute("id", vm.imageNum);
            imgTag.style.maxWidth = 700;
            imgTag.onload = function() {
              vm.imageDragResize();
            };
          }
        });
        this.imageLink = "";
      }
    },

    // execCommand without argument
    // ex. font weight, insert horizontal line
    execCmd(command) {
      window.richTextField.document.execCommand(command, false, null);
      this.setFocus();
    },

    // execCommand with argument
    // ex. insert image or emoji
    execCommandWithArg(command, arg) {
      window.richTextField.document.execCommand(command, false, arg);
      setTimeout(() => {
        this.setFocus();
      }, 10);
    },

    // export to PDF
    async exportToPDF() {
      let today = new Date();
      let year = today.getFullYear();
      let month = today.getMonth() + 1;
      let date = today.getDate();

      // use "html2pdf npm"
      // capture contents of editor
      // change to pdf
      await html2pdf(
        window.richTextField.document.getElementsByTagName("body")[0],
        {
          margin: 10,
          filename: `${year}_${month}_${date}.pdf`,
          image: { type: "jpeg", quality: 0.98 },
          html2canvas: {
            scale: 2,
            // logging: true,
            // dpi: 192,
            // letterRendering: false,
          },
          jsPDF: {
            unit: "mm",
            format: "a4",
            orientation: "portrait",
            precision: 30,
          },
        }
      );
    },

    // export to Word
    exportToWord() {
      let html =
          "<html xmlns:o='urn:schemas-microsoft-com:office:office' xmlns:w='urn:schemas-microsoft-com:office:word' xmlns='http://www.w3.org/TR/REC-html40'><head><meta charset='utf-8'><title>Export HTML To Doc</title></head><body>";
      let footer = "</body></html>";
      let content =
          html +
          window.richTextField.document.getElementsByTagName("body")[0]
              .innerHTML +
          footer;

      // link url
      let url =
          "data:application/vnd.ms-word;charset=utf-8," +
          encodeURIComponent(content);

      // file name
      let filename = "sample_A4" + ".doc";

      // Creates the  download link element dynamically
      let downloadLink = document.createElement("a");

      document.body.appendChild(downloadLink);

      // Link to the file
      downloadLink.href = url;

      // Setting up file name
      downloadLink.download = filename;

      // triggering the function
      downloadLink.click();

      // Remove the a tag after donwload starts.
      document.body.removeChild(downloadLink);
    },
  },

  mounted() {
    this.setLanguage();
    const iframe = window.richTextField.document;
    let vm = this;

    // turn on the design mode
    iframe.designMode = "On";

    // auto line break according to the width
    iframe.getElementsByTagName("body")[0].style.wordBreak = "break-all";
    iframe.getElementsByTagName("body")[0].style.margin = "10px";

    // insert emoji at cursor position
    const picker = new EmojiButton();
    const trigger = document.querySelector("#emoji-trigger");

    picker.on("emoji", (selection) => {
      this.execCommandWithArg("insertHTML", selection.emoji);
    });

    trigger.addEventListener("click", () => picker.togglePicker(trigger));

    // dropdown close with click event
    window.onclick = function(event) {
      if (!event.target.matches(".dropdownButton")) {
        let dropdowns = document.getElementsByClassName("dropdown-content");
        let i;
        for (i = 0; i < dropdowns.length; i++) {
          let openDropdown = dropdowns[i];
          if (openDropdown.classList.contains("show")) {
            openDropdown.classList.remove("show");
          }
        }
      }
      if (event.target === document.getElementById("linkModal")) {
        document.getElementById("linkModal").style.display = "none";
        vm.pageLink = "";
      }
      if (event.target === document.getElementById("imageModal")) {
        document.getElementById("imageModal").style.display = "none";
        vm.imageLink = "";
      }
    };

    iframe.onclick = function(event) {
      if (!event.target.matches(".dropdownButton")) {
        let dropdowns = document.getElementsByClassName("dropdown-content");
        let i;
        for (i = 0; i < dropdowns.length; i++) {
          let openDropdown = dropdowns[i];
          if (openDropdown.classList.contains("show")) {
            openDropdown.classList.remove("show");
          }
        }
      }
    };

    // send updated contents to parent
    jquery('iframe[name="richTextField"]')
      .contents()
      .on("DOMSubtreeModified propertychange", function() {
        const content = window.richTextField.document
          .getElementsByTagName("body")[0]
          .outerHTML.substring(51)
          .slice(0, -7);
        vm.$emit("updateContent", content);
      });

    // receive the contents from parent
    iframe.getElementsByTagName("body")[0].innerHTML = this.content;
  },
};
</script>

<style scoped>
.v-text-field__details {
  display: none !important;
}
.toolButton {
  margin-right: 2px;
  cursor: pointer;
  background-color: white;
  border: none;
  color: black;
  width: 40px;
  height: 40px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  position: relative;
}
.toolButtonText {
  cursor: pointer;
  background-color: white;
  border: none;
  color: black;
  height: 40px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  position: relative;
}
.toolButton:hover {
  background-color: #efefef;
}
.toolButton:hover .tooltip {
  visibility: visible;
}
.tooltip {
  font-size: 13px;
  visibility: hidden;
  width: 70px;
  display: inline;
  background-color: black;
  color: #fff;
  text-align: center;
  padding: 5px 5px 8px 5px;
  border-radius: 6px;
  /* Position the tooltip text - see examples below! */
  position: absolute;
  z-index: 1;
  opacity: 0.8;
  top: 100%;
  left: 50%;
  margin-left: -40px;
}
.tooltip::after {
  content: " ";
  position: absolute;
  bottom: 100%; /* At the top of the tooltip */
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: transparent transparent black transparent;
}

.toolButtonText:hover {
  background-color: #efefef;
}
.toolButtonText:hover .tooltip {
  visibility: visible;
}
.toolButtonText .tooltip {
  font-size: 13px;
  visibility: hidden;
  width: 70px;
  display: inline;
  background-color: black;
  color: #fff;
  text-align: center;
  padding: 5px 5px 8px 5px;
  border-radius: 6px;
  /* Position the tooltip text - see examples below! */
  position: absolute;
  z-index: 1;
  top: 100%;
  opacity: 0.8;
  left: 50%;
  margin-left: -40px;
}
.toolButtonText .tooltip::after {
  content: " ";
  position: absolute;
  bottom: 100%; /* At the top of the tooltip */
  left: 50%;
  margin-left: -5px;
  border-width: 5px;
  border-style: solid;
  border-color: transparent transparent black transparent;
}
.colorPicker {
  cursor: pointer;
  border: none;
}
.colorPickerButton {
  font-size: 14px;
  display: inline-block;
  padding: 0px 5px;
  color: gray;
  -ms-user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
  -webkit-user-select: none;
  user-select: none;
}
.dropdownButton {
  margin-right: 6px;
  border: 1px solid black;
  border-radius: 3px;
  padding: 5px;
  background-color: white;
  cursor: pointer;
}
.dropdownButton:hover .tooltip {
  visibility: visible;
}
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
}
.dropdown-content div {
  cursor: pointer;
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}
.dropdown-content :hover {
  background-color: #f1f1f1;
}
.modal {
  display: none; /* Hidden by default */
  position: fixed; /* Stay in place */
  z-index: 1; /* Sit on top */
  padding-top: 100px; /* Location of the box */
  left: 0;
  top: 0;
  width: 100%; /* Full width */
  height: 100%; /* Full height */
  overflow: auto; /* Enable scroll if needed */
  background-color: rgb(0, 0, 0); /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4); /* Black w/ opacity */
}

/* Modal Content */
.modal-content {
  background-color: #fefefe;
  margin: auto;
  padding: 20px;
  border: 1px solid #888;
  width: 400px;
  border-radius: 10px;
}
.modalButton {
  font-weight: bold;
  font-size: 16px;
  width: 100%;
  padding: 7px;
  border: none;
  border-radius: 5px;
  box-shadow: 1px 1px 1px 0.5px #dadce0;
  background-color: #ececec;
}
.modalButton:hover {
  background-color: #dddddd;
}
.modalTextInput {
  width: 99%;
  margin-bottom: 20px;
  padding: 7px 0;
  font-size: 17px;
}
#richTextField {
  overflow-y: hidden;
  height: 500px;
  border: solid #d1d1d1 1px;
  border-radius: 3px;
}
.editorWidth {
  width: 737px;
}
</style>
