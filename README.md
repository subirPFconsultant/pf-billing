
<!DOCTYPE html>
<html>
<head>
  <title>PF Billing</title>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.9.2/html2pdf.bundle.min.js"></script>

  <style>
    body {
      font-family: Arial;
      background: #f2f2f2;
      padding: 20px;
    }

    .form-box {
      max-width: 400px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
    }

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
    }

    button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      background: green;
      color: white;
      border: none;
    }

    /* PDF Design */
    #invoice {
      display: none;
      padding: 20px;
    }

    .top {
      text-align: center;
    }

    .header {
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
      border-bottom: 2px solid black;
      padding-bottom: 10px;
    }

    .logo {
      width: 80px;
    }

    table {
      width: 100%;
      margin-top: 20px;
      border-collapse: collapse;
    }

    table, th, td {
      border: 1px solid black;
      padding: 8px;
    }

    .qr {
      text-align: center;
      margin-top: 20px;
    }

    .qr img {
      width: 100px;
    }

  </style>
</head>

<body>

<!-- FORM PAGE -->
<div class="form-box">
  <h3>Enter Details</h3>

  <input id="name" placeholder="Customer Name">
  <input id="mobile" placeholder="Mobile Number">
  <input id="uan" placeholder="UAN Number">
  <input id="service" placeholder="Service">
  <input id="amount" placeholder="Amount">

  <select id="status">
    <option>Paid</option>
    <option>Unpaid</option>
  </select>

  <button onclick="downloadPDF()">Download Bill</button>
</div>

<!-- PDF PAGE -->
<div id="invoice">

  <div class="top">
    <img src="https://instasize.com/p/16b63c2748e208b0b90557a642dd499cdd1143cb59d54632908c8efdc80d1654" width="100">
  </div>

  <div class="header">
    <div>
      <h3>PF Consultant Service</h3>
      <p>Address: West Bengal, South 24 Parganas, Namkhana, Patibunia - 743357</p>
      <p>Mobile: 7365996618</p>
      <p>WhatsApp: 9775515990</p>
      <p>Email: subir.das7365@gmail.com</p>
    </div>

    <img src="https://instasize.com/p/16b63c2748e208b0b90557a642dd499cdd1143cb59d54632908c8efdc80d1654" class="logo">
  </div>

  <table>
    <tr>
      <th>Name</th>
      <th>Mobile</th>
      <th>UAN</th>
      <th>Service</th>
      <th>Amount</th>
      <th>Status</th>
    </tr>

    <tr>
      <td id="cname"></td>
      <td id="cmobile"></td>
      <td id="cuan"></td>
      <td id="cservice"></td>
      <td id="camount"></td>
      <td id="cstatus"></td>
    </tr>
  </table>

  <div class="qr">
    <p>QR কোড স্ক্যান করে পেমেন্ট করুন</p>
    <img src="https://instasize.com/p/e90e86d1ff81e24da711315ea0599e19ddbd349457d723b060ba9d4b98ed7ef7">
  </div>

  <p style="text-align:right;">Thank You</p>

</div>

<script>
function downloadPDF() {

  document.getElementById("cname").innerText = document.getElementById("name").value;
  document.getElementById("cmobile").innerText = document.getElementById("mobile").value;
  document.getElementById("cuan").innerText = document.getElementById("uan").value;
  document.getElementById("cservice").innerText = document.getElementById("service").value;
  document.getElementById("camount").innerText = document.getElementById("amount").value;
  document.getElementById("cstatus").innerText = document.getElementById("status").value;

  let invoice = document.getElementById("invoice");
  invoice.style.display = "block";

  html2pdf().from(invoice).save("PF_Bill.pdf");

  invoice.style.display = "none";
}
</script>

</body>
</html>
