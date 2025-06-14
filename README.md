# ska-2025
Survei Kepuasan Al Abidin 2025
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Progress } from "@/components/ui/progress";

export default function SurveyPage() {
  const [submitted, setSubmitted] = useState(false);
  const [step, setStep] = useState(0);
  const totalSteps = 10;

  const sekolahList = [
    "TKII Al Abidin Surakarta",
    "TKQP Colomadu Karanganyar",
    "SDII Al Abidin Surakarta",
    "SDTQ Al Abidin Surakarta",
    "SDICT Al Abidin Surakarta",
    "SDII Al Abidin Sragen",
    "SMPI Al Abidin Surakarta",
    "SMA ABBS Surakarta",
    "TKII Al Abidin Boyolali",
    "SDII Al Abidin Boyolali",
    "SMPII Al Abidin Boyolali",
    "TKII Al Abidin Sukoharjo",
    "SDII Al Abidin Sukoharjo",
    "SMPII Al Abidin Sukoharjo",
    "TKII Al Abidin Karanganyar",
    "SDII Al Abidin Karanganyar",
    "SMPII Al Abidin Karanganyar",
    "SMP ABBS Surakarta",
    "TKII Al Abidin Klaten",
    "SDII Al Abidin Klaten",
    "SMPII Al Abidin Klaten",
    "TKII Al Abidin Yogyakarta",
    "SDII Al Abidin Yogyakarta",
    "SMPII Al Abidin Yogyakarta"
  ];

  const [jenjang, setJenjang] = useState("");
const formSteps = [
    {
      title: "Informasi Responden",
      content: (
        <div className="space-y-4">
          <div>
            <label className="block mb-1">Nama Anak</label>
            <Input placeholder="Contoh: Ahmad Zidan" required />
          </div>
          <div>
          <label className="block mb-1">Jenjang</label>
          <select className="w-full border rounded p-2" required onChange={(e) => setJenjang(e.target.value)}>
            <option value="">-- Pilih Jenjang --</option>
            <option value="TK">TK</option>
            <option value="SD">SD</option>
            <option value="SMP">SMP</option>
            <option value="SMA">SMA</option>
          </select>
        </div>

        {jenjang && (
          <div>
            <label className="block mb-1">Kelas</label>
            <select className="w-full border rounded p-2" required>
              <option value="">-- Pilih Kelas --</option>
              {jenjang === "TK" && ["KB", "TK A", "TK B"].map(k => (
                <option key={k} value={k}>{k}</option>
              ))}
              {jenjang === "SD" && [1,2,3,4,5,6].map(k => (
                <option key={k} value={`Kelas ${k}`}>Kelas {k}</option>
              ))}
              {jenjang === "SMP" && [7,8,9].map(k => (
                <option key={k} value={`Kelas ${k}`}>Kelas {k}</option>
              ))}
              {jenjang === "SMA" && [10,11,12].map(k => (
                <option key={k} value={`Kelas ${k}`}>Kelas {k}</option>
              ))}
            </select>
          </div>
        )}

        <div>
  <label className="block mb-1">Nama Sekolah</label>
  <select className="w-full border rounded p-2" required>
    <option value="">-- Pilih Sekolah --</option>
    {jenjang === "TK" && [
      "TKII Al Abidin Surakarta",
      "TKQP Colomadu Karanganyar",
      "TKII Al Abidin Boyolali",
      "TKII Al Abidin Sukoharjo",
      "TKII Al Abidin Karanganyar",
      "TKII Al Abidin Klaten",
      "TKII Al Abidin Yogyakarta"
    ].map((sekolah) => (
      <option key={sekolah} value={sekolah}>{sekolah}</option>
    ))}
    {jenjang === "SD" && [
      "SDII Al Abidin Surakarta",
      "SDTQ Al Abidin Surakarta",
      "SDICT Al Abidin Surakarta",
      "SDII Al Abidin Sragen",
      "SDII Al Abidin Boyolali",
      "SDII Al Abidin Sukoharjo",
      "SDII Al Abidin Karanganyar",
      "SDII Al Abidin Klaten",
      "SDII Al Abidin Yogyakarta"
    ].map((sekolah) => (
      <option key={sekolah} value={sekolah}>{sekolah}</option>
    ))}
    {jenjang === "SMP" && [
      "SMPI Al Abidin Surakarta",
      "SMPII Al Abidin Boyolali",
      "SMPII Al Abidin Sukoharjo",
      "SMPII Al Abidin Karanganyar",
      "SMP ABBS Surakarta",
      "SMPII Al Abidin Klaten",
      "SMPII Al Abidin Yogyakarta"
    ].map((sekolah) => (
      <option key={sekolah} value={sekolah}>{sekolah}</option>
    ))}
    {jenjang === "SMA" && ["SMA ABBS Surakarta"].map((sekolah) => (
      <option key={sekolah} value={sekolah}>{sekolah}</option>
    ))}
  </select>
</div>
          <div>
            <label className="block mb-1">Jumlah Anak di Sekolah Ini</label>
            <Input type="number" placeholder="Contoh: 2" required />
          </div>
        </div>
      )
    },
    {
      title: "1. Pelayanan Umum",
      content: [
        "Staf administrasi melayani dengan ramah dan sigap",
        "Proses administrasi berjalan lancar",
        "Petugas keamanan bersikap sopan dan responsif",
        "Kebersihan area sekolah terjaga dengan baik"
      ]
    },
    {
      title: "2. Kurikulum dan Pembelajaran",
      content: [
        "Metode pembelajaran sesuai dengan kebutuhan anak",
        "Guru mengajar dengan kompeten",
        "Tugas dan evaluasi diberikan secara proporsional",
        "Pembelajaran menyenangkan dan memotivasi anak"
      ]
    },
    {
      title: "3. Perkembangan Anak",
      content: [
        "Anak mengalami perkembangan karakter yang baik",
        "Sekolah mendukung akademik anak",
        "Anak menjadi lebih percaya diri",
        "Anak didorong untuk mandiri dan bertanggung jawab"
      ]
    },
    {
      title: "4. Komunikasi Sekolah-Orang Tua",
      content: [
        "Informasi disampaikan jelas dan tepat waktu",
        "Guru mudah dihubungi",
        "Orang tua dilibatkan dalam kegiatan sekolah",
        "Ada wadah komunikasi dua arah antara sekolah dan orang tua"
      ]
    },
    {
      title: "5. Fasilitas dan Keamanan",
      content: [
        "Fasilitas sekolah memadai",
        "Keamanan anak terjamin",
        "Ruang kelas nyaman dan bersih",
        "Lingkungan sekolah mendukung kegiatan belajar"
      ]
    },
    {
      title: "6. Kegiatan & Program Unggulan",
      content: [
        "Kegiatan mendukung potensi anak",
        "Program unggulan sesuai harapan",
        "Anak antusias mengikuti program tambahan",
        "Sekolah memiliki variasi kegiatan ekstrakurikuler yang menarik"
      ]
    },
    {
      title: "7. Biaya Pendidikan",
      content: [
        "Biaya sesuai dengan layanan yang diberikan",
        "Biaya sekolah transparan",
        "Sekolah memberikan informasi tagihan secara tepat waktu",
        "Ada fleksibilitas atau bantuan untuk orang tua yang membutuhkan"
      ]
    },
    {
      title: "Refleksi dan Saran",
      content: (
        <div className="space-y-4">
          <div>
            <label className="block mb-1">Apa yang paling Anda sukai dari sekolah ini?</label>
            <Textarea rows={3} required />
          </div>
          <div>
            <label className="block mb-1">Apa saran Anda untuk perbaikan layanan sekolah?</label>
            <Textarea rows={3} required />
          </div>
        </div>
      )
    }
  ];

  const handleNext = () => setStep(prev => Math.min(prev + 1, formSteps.length));
  const handleBack = () => setStep(prev => Math.max(prev - 1, 0));

  const handleSubmit = (e) => {
    e.preventDefault();
    const data = new FormData(e.target);
    const entries = {};
    for (let [key, value] of data.entries()) {
      entries[key] = value;
    }

    const csvContent = `data:text/csv;charset=utf-8,${Object.keys(entries).join(',')}
${Object.values(entries).join(',')}`;
    const encodedUri = encodeURI(csvContent);
    const link = document.createElement("a");
    link.setAttribute("href", encodedUri);
    link.setAttribute("download", "hasil_survei.csv");
    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);

    setSubmitted(true);
  };

  return (
    <div className="max-w-3xl mx-auto p-6 space-y-6">
      <h1 className="text-3xl font-bold text-center text-indigo-700">
        Survei Kepuasan Orang Tua
      </h1>

      <div className="text-sm text-gray-700 bg-yellow-50 border border-yellow-300 rounded p-4">
        <p className="mb-2">
          Survei ini bertujuan untuk mengetahui tingkat kepuasan orang tua terhadap
          layanan pendidikan di sekolah-sekolah Al Abidin. Hasil dari survei ini akan
          digunakan sebagai dasar evaluasi dan peningkatan mutu layanan kami.
        </p>
        <ul className="list-disc list-inside mb-2">
          <li>Survei terdiri dari 7 dimensi penilaian.</li>
          <li>Jawaban Anda bersifat rahasia dan hanya untuk keperluan internal.</li>
          <li>Mohon mengisi setiap pertanyaan dengan jujur dan lengkap.</li>
        </ul>
        <p>Terima kasih atas partisipasi Anda!</p>
      </div>

      <Progress value={((step + 1) / formSteps.length) * 100} className="h-3 bg-gray-200" />

      <form onSubmit={handleSubmit}>
        <Card className="shadow-lg border border-indigo-200">
          <CardContent className="space-y-4 p-6 bg-gradient-to-br from-blue-50 via-white to-pink-50 rounded-xl">
            <h2 className="text-lg font-semibold text-blue-800 border-b pb-2">
              {formSteps[step].title}
            </h2>

            {Array.isArray(formSteps[step].content)
              ? formSteps[step].content.map((item, idx) => (
                  <div key={idx} className="bg-white border border-gray-200 rounded p-3 mb-4 shadow-sm">
                    <label className="block mb-2 font-medium text-gray-700">{item}</label>
                    <div className="flex flex-col space-y-2 pl-2">
                      {[1, 2, 3, 4, 5].map(val => (
                        <label key={val} className="flex items-center space-x-2 text-sm text-gray-700">
                          <input type="radio" name={item} value={val} required className="accent-indigo-600" />
                          <span className="text-gray-800">{val} - {['Sangat Tidak Puas', 'Tidak Puas', 'Cukup', 'Puas', 'Sangat Puas'][val - 1]}</span>
                        </label>
                      ))}
                    </div>
                  </div>
                ))
              : formSteps[step].content}

            <div className="flex justify-between pt-4">
              {step > 0 && (
                <Button variant="outline" onClick={handleBack} className="text-gray-600 hover:bg-gray-100">Kembali</Button>
              )}
              {step < formSteps.length - 1 ? (
                <Button type="button" onClick={handleNext} className="bg-indigo-600 hover:bg-indigo-700 text-white">Lanjut</Button>
              ) : (
                <Button type="submit" className="bg-green-600 hover:bg-green-700 text-white">Kirim Survei</Button>
              )}
            </div>
          </CardContent>
        </Card>
      </form>
    </div>
  );
}
